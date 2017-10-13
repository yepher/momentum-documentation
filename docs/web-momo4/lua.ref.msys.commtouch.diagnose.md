| msys.commtouch.diagnose |
| [Prev](lua.ref.msys.cidr.reload.php)  | Chapter 70. Lua Functions Reference |  [Next](lua.ref.msys.counter.add.php) |

<a name="lua.ref.msys.commtouch.diagnose"></a>
## Name

msys.commtouch.diagnose — Scan messages using Commtouch

<a name="idp17752048"></a>
## Synopsis

`msys.commtouch.diagnose(msg, accept, vctx);`

```
msg: userdata, ec_message type, optional
accept: userdata, accept_construct type, optional
vctx: userdata, validate_context type, optional
```
<a name="idp17755168"></a>
## Description

This function provides diagnosis of a message's virus or spam status. You must load and correctly configure the commtouch_ctasd module before using this function. For details, see [Section 71.20, “commtouch_ctasd – Commtouch Spam Protection”](modules.commtouch.php "71.20. commtouch_ctasd – Commtouch Spam Protection").

It can be invoked at the data, spool, or each_rcpt phases, and it will not work at the connect, ehlo, mailfrom, or rcptto phases.

Enable this function with the statement `require('msys.commtouch');`.

It takes the following parameters. If any of the inputs is not provided, it will be inferred from the current context:

*   `msg` – Email to be scored

*   `accept` – accept_construct

*   `vctx` – Validation context

This function returns a table with the following key/value pairs:

*   `class` – Spam classification of this message. Possible values are `Unknown`, `Suspected`, `Bulk`, and `Spam`.

*   `virus-threat` – Virus classification of this message. Possible values are `non-virus`, `medium`, `high`, and `virus`.

*   `ref-id` – Reference ID returned by the commtouch engine.

The above name value pairs are also set within the validation context with each key being prefixed with `commtouch-`.

### Warning

Do not use `pcall` with this function.

| [Prev](lua.ref.msys.cidr.reload.php)  | [Up](lua.function.details.php) |  [Next](lua.ref.msys.counter.add.php) |
| msys.cidr.reload  | [Table of Contents](index.php) |  msys.counter.add |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)