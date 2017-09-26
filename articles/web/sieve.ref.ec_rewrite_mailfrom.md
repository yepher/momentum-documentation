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

| ec_rewrite_mailfrom |
| [Prev](sieve.ref.ec_rand.php)  | Chapter 15. Sieve++ Function Reference |  [Next](sieve.ref.ec_rfc2047_encode_addresses.php) |

<a name="sieve.ref.ec_rewrite_mailfrom"></a>
## Name

ec_rewrite_mailfrom — change the envelope sender

## Synopsis

`ec_rewrite_mailfrom` { *`address`* } [ *`counter`* ]

<a name="idp15110256"></a>
## Description

**Configuration Change. ** This feature was introduced in Momentum 2.1.

This action will replace the envelope sender (the `MAIL FROM`) address on the envelope with the one supplied. The headers and the body of the message will not be changed.

The optional counter parameter to `ec_rewrite_mailfrom` is used to count the number of hits for this particular action; if omitted, the script filename and line number will be assumed. You can see the hit count via the web console or via **ec_console** using the **sieve stats**       command.

Sieve scripts using `ec_rewrite_mailfrom` can be set during data_phase1 or any subsequent phase except the set_binding_phase.

<a name="example.ec_rewrite_mailfrom"></a>

**Example 15.87. ec_rewrite_mailfrom example**

```
if envelope :domain :is "from" "bar.com" {
  ec_rewrite_mailfrom "bar@foo.com";
  stop;
}
```

| [Prev](sieve.ref.ec_rand.php)  | [Up](sieve.ref.php) |  [Next](sieve.ref.ec_rfc2047_encode_addresses.php) |
| ec_rand  | [Table of Contents](index.php) |  ec_rfc2047_encode_addresses |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)