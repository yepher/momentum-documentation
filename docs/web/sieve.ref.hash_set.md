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

| hash_set |
| [Prev](sieve.ref.hash_keys.php)  | Chapter 15. Sieve++ Function Reference |  [Next](sieve.ref.hash_values.php) |

<a name="sieve.ref.hash_set"></a>
## Name

hash_set — set an element in a hash

## Synopsis

`hash_set` { *`hash`* } { *`key`* } { *`value`* }

<a name="idp15693728"></a>
## Description

**Configuration Change. ** This feature was introduced in Momentum 2.1.1.

This function sets a value in a hash table for a particular key. Hash keys must be strings (but can be expressions that resolve to strings), whereas hash values can be any valid Sieve value (string, number, stringlist or hashes).

### Note

In version 2.2 this feature requires that the sievelib module be loaded.

<a name="example.set"></a>

**Example 15.110. hash_set example**

```
$hash = hash_create;
hash_set $hash "mykey" "myvalue";
$value = $hash["mykey"];

ec_log "The value is ${value}";
```

<a name="idp15702736"></a>
## See Also

[hash_create](sieve.ref.hash_create.php "hash_create"), [hash_dump](sieve.ref.hash_dump.php "hash_dump") and [hash_get](sieve.ref.hash_get.php "hash_get").

| [Prev](sieve.ref.hash_keys.php)  | [Up](sieve.ref.php) |  [Next](sieve.ref.hash_values.php) |
| hash_keys  | [Table of Contents](index.php) |  hash_values |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)