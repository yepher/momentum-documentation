| domainkeys |
| [Prev](conf.ref.domain.php)  | Chapter 72. Configuration Options Reference |  [Next](conf.ref.drop_body_after_trans_fail.php) |

<a name="conf.ref.domainkeys"></a>
## Name

domainkeys — enable or disable domainkeys signing

## Synopsis

`domainkeys = "enabled"`
`domainkeys = "disabled"`

<a name="idp24486480"></a>
## Description

This directive instructs Momentum to enable (or disable) signing messages with a DomainKeys signature globally, on a specific domain, binding, or domain within a binding. To use this directive, you must also configure the [`dk_sign`](modules.domainkeys.php "71.28. domainkeys – Yahoo! DomainKeys") module. When the dk_sign module is loaded, signing occurs for all messages by default. This is the same as setting `domainkeys = "enabled"` at the global scope.

<a name="idp24489936"></a>
## Scope

domainkeys is valid in the binding, binding_group, domain, and global scope.

| [Prev](conf.ref.domain.php)  | [Up](config.options.ref.php) |  [Next](conf.ref.drop_body_after_trans_fail.php) |
| domain  | [Table of Contents](index.php) |  drop_body_after_trans_fail |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)