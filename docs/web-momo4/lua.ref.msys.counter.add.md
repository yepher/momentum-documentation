| msys.counter.add |
| [Prev](lua.ref.msys.commtouch.diagnose.php)  | Chapter 70. Lua Functions Reference |  [Next](lua.ref.msys.counter.inc.php) |

<a name="lua.ref.msys.counter.add"></a>
## Name

msys.counter.add — Add to the current value of the specified counter

<a name="idp17778752"></a>
## Synopsis

`msys.counter.add(object_or_path, delta);`

```
object_or_path: mixed
delta: number
```
<a name="idp17781712"></a>
## Description

The first argument is either a path to a counter (for example, `/sites/site_name/errors`) or a counter object that was returned by `msys.counter.open`. If a string is provided containing the path to a counter that does not exist, the counter is created with STRICT semantics. The second argument is atomically added to the current value of the counter.

Enable this function with the statement `require('msys.counter');`. For a code example, see [Example 70.54, “msys.counter.read example”](lua.ref.msys.counter.read.php#lua.ref.msys.counter.read.example "Example 70.54. msys.counter.read example").

You can also use the [counter](console_commands.counter.php "counter") console command to display and manipulate counters.

<a name="idp17787376"></a>
## See Also

[msys.counter.reset](lua.ref.msys.counter.reset.php "msys.counter.reset"), [msys.counter.inc](lua.ref.msys.counter.inc.php "msys.counter.inc"), [msys.counter.open](lua.ref.msys.counter.open.php "msys.counter.open"), [msys.counter.unlink](lua.ref.msys.counter.unlink.php "msys.counter.unlink")

| [Prev](lua.ref.msys.commtouch.diagnose.php)  | [Up](lua.function.details.php) |  [Next](lua.ref.msys.counter.inc.php) |
| msys.commtouch.diagnose  | [Table of Contents](index.php) |  msys.counter.inc |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)