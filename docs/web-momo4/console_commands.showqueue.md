| showqueue |
| [Prev](console_commands.show_outbound.php)  | Chapter 73. Non-Module-Specific Console Commands |  [Next](console_commands.shutdown.php) |

<a name="console_commands.showqueue"></a>
## Name

showqueue — show queue information

## Synopsis

`showqueue` [ binding *`binding_name`* ] { *`domain_name`* } [ *`limit,offset`* ]

<a name="idp13798560"></a>
## Description

The **showqueue** command is used to list the messages in the queue for a particular domain. The first optional argument is the binding name. If no binding is specified, the default binding will be used. A domain name must be specified. The final optional argument is a "maximum" to show and an "offset" at which to start displaying. This argument defaults to "100,0" if omitted.

To display all the bindings on a domain execute the command **showqueue binding all *`example.com`***                             .

The output from the domain example.com which has one message in the active queue and one in the delayed queue, both destined to leave via the default binding, might look as follows:

```
10:47:35 /tmp/2025> showqueue example.com
[active/default] B3/1D-18426-471AACF3 Created: 1070244212
  From: <sender@postalengine.com> To: <rcpt1@example.com>
[delayed/default] B3/79-18426-4A4BACF3 Created: 1070244212
  From: <sender@postalengine.com> To: <rcpt2@example.com>
```

you can also list the messages in the queue for a particular domain on a particular binding by specifying a binding name as shown in the following example:

```
10:47:35 /tmp/2025> showqueue binding smtp-01 example.com
[active/smtp-01] 00/00-21047-B5581944 Created: 1150387547
  From: <sender@example.com> To: <rcpt2@example.com>
[delayed/smtp-01] 10/00-21047-B5581944 Created: 1150387547
  From: <sender@example.com> To: <rcpt1@example.com>
```

| [Prev](console_commands.show_outbound.php)  | [Up](console.cmds.ref.php) |  [Next](console_commands.shutdown.php) |
| show outbound  | [Table of Contents](index.php) |  shutdown |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)