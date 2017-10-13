| msys.httpsrv.register |
| [Prev](lua.ref.msys.getClassMetaTable.php)  | Chapter 70. Lua Functions Reference |  [Next](lua.ref.msys.idn.php) |

<a name="lua.ref.msys.httpsrv.register"></a>
## Name

msys.httpsrv.register — Register a Lua function as an HTTP endpoint

<a name="idp16140512"></a>
## Synopsis

`require("msys.httpsrv");`

`msys.httpsrv.register(method, endpoint, function_name);`

```
method: string
endpoint: string
function_name: string
```
<a name="idp16144288"></a>
## Description

Use this function to register a Lua function as an HTTP endpoint. You can register the same endpoint multiple times with different methods:

```
msys.httpsrv.register(“GET”, “/somepath”, my_endpoint)
msys.httpsrv.register(“POST”, “/somepath”, my_endpoint)
```

A Lua function registered in this way has access to the HTTP session object. For a description of the session object, see [ec_httpsrv_session](https://support.messagesystems.com/docs/web-c-api/structs.ec_httpsrv_session.php).

The `function_name` Lua function is called when a HTTP request is made matching the `method` HTTP method and `endpoint` base URI path.

Method can be nil, meaning “all methods”. Although, this setting is unlikely in practice.

Note that the trailing slash '/' character is optional on endpoint handlers.

<a name="lua.ref.msys.httpsrv.register.example"></a>

**Example 70.30. msys.httpsrv.register Example**

```
require("msys.extended.httpsrv")
require("msys.core")

local mod = {}

-- HTTP endpoint
function mysimple_handler(session)
  local url_details = session:request_url_get()
  local response = url_details.url .. " says: Hello world!"
  session:response_status_set_std(200, response, "text/plain")
end

--Console command
local function delay_domain(cc)
  -- Check the number of parameters
  if cc.argc < 2 then
   print("You must pass a parameter to this command");
   return;
  end
  local domain = cc.argv[1];
  local dr = msys.core.dns_get_domain(domain);
  if dr ~= nil then
    msys.core.mail_queue_delay_domain(dr, "451 4.4.1 [internal] manually delayed domain]");
    print(domain, "added to the delayed queue.");
  end
end

function mod:rsrc_setup()
  msys.httpsrv.register("POST", "/somepath", mysimple_handler)
  msys.registerControl("some_command", delay_domain)
  return true
end

msys.registerModule("example", mod)
```

### Note

The `rsrc_setup` hook provides a safer way to register resources against new [config](console_commands.config.php "config") actions. Note that this example shows how to register an ec_console command as well as a custom HTTP endpoint. In Momentum 4, use the code shown here rather than the code shown in the [msys.registerControl](lua.ref.msys.registerControl.php "msys.registerControl") example.

<a name="idp16158512"></a>
## See Also

[session:request_url_get](lua.ref.session_request_url_get.php "session:request_url_get") and [session:response_status_set_std](lua.ref.session_response_status_set_std.php "session:response_status_set_std")

| [Prev](lua.ref.msys.getClassMetaTable.php)  | [Up](lua.function.details.php) |  [Next](lua.ref.msys.idn.php) |
| msys.getClassMetaTable  | [Table of Contents](index.php) |  msys.idn.to_idn |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)