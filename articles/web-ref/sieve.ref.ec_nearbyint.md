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

| ec_nearbyint |
| [Prev](sieve.ref.ec_mul.php)  | 16.2. Sieve Function Details |  [Next](sieve.ref.ec_pcre_match.php) |

<a name="sieve.ref.ec_nearbyint"></a>
## Name

ec_nearbyint — round to the nearest integer based on rounding direction

## Synopsis

`ec_nearbyint` { *`number`* }

<a name="idp30346896"></a>
## Description

`ec_nearbyint` rounds the given number to the nearest integer based on rounding direction.

<a name="example.ec_nearbyint"></a>

**Example 16.84. ec_nearbyint example**

```
$a = 65.43;
$b = -41.65;
$c = 43;
$nearbyinta = ec_nearbyint $a;
$nearbyintb = ec_nearbyint $b;
$nearbyintc = ec_nearbyint $c;
#nearbyinta is 65.000000
#nearbyintb is -42.000000
#nearbyintc is 43.000000
```

| [Prev](sieve.ref.ec_mul.php)  | [Up](sieve.ref.files.php) |  [Next](sieve.ref.ec_pcre_match.php) |
| ec_mul  | [Table of Contents](index.php) |  ec_pcre_match |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)