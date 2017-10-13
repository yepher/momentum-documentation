| bounce_domains |
| [Prev](conf.ref.bounce_behavior.php)  | Chapter 72. Configuration Options Reference |  [Next](conf.ref.bounce_pattern.php) |

<a name="conf.ref.bounce_domains"></a>
## Name

bounce_domains — configure the list of domains eligible for bounce processing by Momentum.

## Synopsis

`Bounce_Domains = ("*.example.com" "example.net")`

<a name="idp23733088"></a>
## Description

When configured as an inbound mail relay, it is necessary to set this option to have mail delivery notifications be reported as bounces. Momentum will treat the listed domains as relay domains in that it will accept mail destined for them and offer them up to internal bounce classification systems and/or loggers. This option can be further qualified with the `Bounce_Pattern` configuration setting and the ultimate behavior of bounce handling is dictated by the the `Bounce_Behavior` configuration setting.

With the `Bounce_Domains` option, you may specify a list of domains and left-globbed domains for which the instance will process as possible bounces. Left-globbed domains are of the form `*fixed.ending`. `*.omniti.com` would **not** match omniti.com (as the dot is required), but would match test.omniti.com, mail.omniti.com, foo.omniti.com, etc. `*omniti.com` would match omniti.com. However, it would also match badomniti.com, which is usually undesirable, so in most cases the asterisk should be followed by a period.

To accept mail for the domain example.com and all subdomains under it, one would specify

`Bounce_Domains = ( "example.com" "*.example.com" )`<a name="idp23740944"></a>
## Scope

bounce_domains is valid in the global, pathway_group and pathway scopes.

<a name="idp23742816"></a>
## See Also

[bounce_pattern](conf.ref.bounce_pattern.php "bounce_pattern"), [bounce_behavior](conf.ref.bounce_behavior.php "bounce_behavior"), [bounce_suppress_list](conf.ref.bounce_suppress_list.php "bounce_suppress_list"), and [Section 71.13, “bounce_logger – Momentum-Style Bounce Logging”](modules.bounce_logger.php "71.13. bounce_logger – Momentum-Style Bounce Logging")

| [Prev](conf.ref.bounce_behavior.php)  | [Up](config.options.ref.php) |  [Next](conf.ref.bounce_pattern.php) |
| bounce_behavior  | [Table of Contents](index.php) |  bounce_pattern |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)