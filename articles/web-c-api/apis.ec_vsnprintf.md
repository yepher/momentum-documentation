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

| ec_vsnprintf |
| [Prev](apis.ec_vprintf.php)  | Chapter 51. String Functions |  [Next](apis.string_destroy.php) |

<a name="apis.ec_vsnprintf"></a>
## Name

ec_vsnprintf — Momentum vsnprintf function

## Synopsis

`#include "misc/ec_string.h"`

| `int **ec_vsnprintf** (` | <var class="pdparam">str</var>, |   |
|   | <var class="pdparam">size</var>, |   |
|   | <var class="pdparam">fmt</var>, |   |
|   | <var class="pdparam">ap</var>`)`; |   |

`char * <var class="pdparam">str</var>`;
`size_t <var class="pdparam">size</var>`;
`const char * <var class="pdparam">fmt</var>`;
`va_list <var class="pdparam">ap</var>`;<a name="idp35411632"></a>
## Description

### Note

This reference page was automatically generated from functions found in the header files in the development branch. The function described here may not exist in generally available versions of Momentum, and may change in behavior when it is generally available. Consult your vendor for definitive advice on the use of this function.

Momentum vsnprintf function.

Private version of vsnprintf() with consistent format string support and return value.

**Parameters**

<dl class="variablelist">

<dt>str</dt>

<dd>

the string to be written to

</dd>

<dt>size</dt>

<dd>

the size of str (including the terminating NUL)

</dd>

<dt>fmt</dt>

<dd>

the format string

</dd>

<dt>ap</dt>

<dd>

list of arguments

</dd>

</dl>

**Return Values**

Returns the number of characters it tried to write. If this value is >= size, truncation ocurred. Note that str is always NUL-terminated as long as size is > 0.

| [Prev](apis.ec_vprintf.php)  | [Up](string.php) |  [Next](apis.string_destroy.php) |
| ec_vprintf  | [Table of Contents](index.php) |  string_destroy |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)