| 37.5. Creating Custom Console Commands |
| [Prev](modules.options.console.php)  | Chapter 37. Using the System Console (**ec_console**) |  [Next](cluster.config.operations.php) |

## 37.5. Creating Custom Console Commands

In addition to the built-in console commands, you can create your own commands using the Lua function [msys.registerControl](lua.ref.msys.registerControl.php "msys.registerControl"). If, for example, you have domains that are heavily throttled and discard messages that are over the limit, you can create a console command to push emails for these domains into the delayed queue:

<a name="operations.console.lua.registerControl"></a>

**Example 37.1. Create console command**

```
require("msys.core");

local function delay_domain(cc)
  local domain = cc.argv[1];
  local dr = msys.core.dns_get_domain(domain);

  if dr ~= nil then
    print ("Domain delayed as requested");
    msys.core.mail_queue_delay_domain(dr, "451 4.4.1 [internal] manually delayed domain");
  end
end

msys.registerControl("delay_domain", delay_domain);
```

This code creates the ec_console command: **delay_domain *`domain`***           .

| [Prev](modules.options.console.php)  | [Up](operations.php) |  [Next](cluster.config.operations.php) |
| 37.4. Setting and Getting Module Options from the Console  | [Table of Contents](index.php) |  Chapter 38. Using the Cluster Manager (**eccmgr**) |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)