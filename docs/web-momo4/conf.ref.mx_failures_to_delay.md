| mx_failures_to_delay |
| [Prev](conf.ref.mx_failures_fallback_to_a.php)  | Chapter 72. Configuration Options Reference |  [Next](conf.ref.never_attempt_expired_messages.php) |

<a name="conf.ref.mx_failures_to_delay"></a>
## Name

mx_failures_to_delay — number of consecutive failures before a domain is auto-delayed

## Synopsis

`mx_failures_to_delay = 50`

<a name="idp25605792"></a>
## Description

When Momentum detects that a domain has no contactable MXs, it will move all that domain's active messages into the delayed queue. This setting allows you to configure the sensitivity of Momentum to consecutive connection failures. Momentum will need `mx_failures_to_delay` consecutive failures for every MX in a domain to trigger a delay event. The default value is 50\. This is configurable both at a global and per-domain level. Setting this value to zero will disable the auto-delay feature.

### Warning

This is an advanced option. Making Momentum too sensitive to transient network connection problems will cause unnecessary delays in message delivery. Thorough testing is recommended prior to deployment in a production environment.

<a name="idp25609680"></a>
## Scope

`mx_failures_to_delay` is valid in the domain and global scopes.

| [Prev](conf.ref.mx_failures_fallback_to_a.php)  | [Up](config.options.ref.php) |  [Next](conf.ref.never_attempt_expired_messages.php) |
| mx_failures_fallback_to_a  | [Table of Contents](index.php) |  never_attempt_expired_messages |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)