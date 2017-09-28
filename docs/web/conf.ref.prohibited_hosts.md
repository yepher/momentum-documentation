Logged in as: OmniTI, Inc.  ([logout](https://support.messagesystems.com/logout.php))

[![Message Systems](https://support.messagesystems.com/images/ms-white205.png)](https://support.messagesystems.com/start.php) 

*   [Changelog](https://support.messagesystems.com/start.php?show=changelog)
*   [Documentation](https://support.messagesystems.com/docs/)
*   [Downloads](https://support.messagesystems.com/start.php)

*   [Licenses](https://support.messagesystems.com/license_summary.php)
*   <a href="">Clients</a>
    *   [Support](https://support.messagesystems.com/cs.php)
    *   [Add/Edit](https://support.messagesystems.com/edit_client.php)
    *   [Legal/Products](https://support.messagesystems.com/edit_products.php)
*   [Users](https://support.messagesystems.com/edit_customer.php)

## Search Help

Search for a single word or perform multi-word searches by enclosing your search in quotation marks.

Where you have multiple words but no quotation marks, an **OR** search is performed. For example, **"REST Injection"** searches for the phrase **"REST Injection"**, and, without quotation marks, searches for **REST OR Injection**--the operator is understood.

### Warning

You must escape the following special characters: **+ - && || ! ( ) { } [ ] ^ " ~ * ? : \**. Use the **\** character as the escape character. For example: **B0/00-11719-46C328D4\:default\:**

You can also perform **AND** searches, for example, **rest AND port** (no quotation marks) finds pages where both these words occur.

Terms used in searches are case-insensitive but operators are not. Alphabetic operators **must** be in uppercase.

Other operators can also be used. For more information see "[Query Parser Syntax](https://lucene.apache.org/core/old_versioned_docs/versions/3_0_0/queryparsersyntax.html)". Use of fields in searches is not currently supported.

| prohibited_hosts |
| [Prev](conf.ref.pidfile.php)  | 9.2. Configuration Files and Option Details |  [Next](conf.ref.rcptto_timeout.php) |

<a name="conf.ref.prohibited_hosts"></a>
## Name

prohibited_hosts — prevent mail from being delivered to invalid destinations

## Synopsis

`Prohibited_Hosts = ("127.0.0.1")`

`Prohibited_Hosts = ("127.0.0.1" "fe80::a00:1")`

<a name="idp6233120"></a>
## Description

Some providers use DNS tricks to deter systems they feel are abusing their resources. One technique is to return a loopback or other local address to you when you query their MX records.

There are some addresses you may never want to deliver mail to. For example, when configured as an outbound e-mail relay you have no reason to deliver mail to your own ip, or any loopback addresses on your machine. To prevent delivery to loopback addresses (127.0.0.0/8) or the null route 0.0.0.0, you can use the following line:

`Prohibited_Hosts = ( "127.0.0.0/8" "0.0.0.0" )`
### Note

Note: This setting does not in any way affect where you can receive mail from, only where you can deliver mail to.

<a name="idp6237328"></a>
## Scope

prohibited_hosts is valid in the global scope.

| [Prev](conf.ref.pidfile.php)  | [Up](conf.ref.files.php) |  [Next](conf.ref.rcptto_timeout.php) |
| pidfile  | [Table of Contents](index.php) |  rcptto_timeout |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)