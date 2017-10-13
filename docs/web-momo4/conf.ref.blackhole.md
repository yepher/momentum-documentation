| blackhole |
| [Prev](conf.ref.binding_group.php)  | Chapter 72. Configuration Options Reference |  [Next](conf.ref.body_timeout.php) |

<a name="conf.ref.blackhole"></a>
## Name

blackhole — blackhole mail

## Synopsis

`Blackhole = "false"`

`Blackhole = "true"`

`Blackhole = "inline"`

`Blackhole = "internal"`

<a name="idp23674720"></a>
## Description

This option may be specified globally or inside a `domain`, `binding_group` or `binding` stanza. If specified in the domain scope, Momentum immediately fails all messages queued for that domain. Likewise, if it is specified in the binding or binding_group scope. If `Generate_Bounces` is true, then a bounce message will be generated for each message failed.

If this option is set to `inline`, messages are failed permanently during the SMTP transaction (upon reception), immediately after receiving the RCPT TO command.

If `internal` is specified, the message is accepted and internally dropped. The normal message failure operations such as logging, still take place.

The default value for this option is `false`. Specifying `true` is equivalent to specifying `inline`.

<a name="idp23682528"></a>
## Scope

Blackhole is valid in the binding, binding_group, domain and global scopes.

<a name="idp23684400"></a>
## See Also

[bounce_behavior](conf.ref.bounce_behavior.php "bounce_behavior"), [generate_bounces](conf.ref.generate_bounces.php "generate_bounces")

| [Prev](conf.ref.binding_group.php)  | [Up](config.options.ref.php) |  [Next](conf.ref.body_timeout.php) |
| binding_group  | [Table of Contents](index.php) |  body_timeout |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)