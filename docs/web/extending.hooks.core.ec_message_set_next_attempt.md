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

| ec_message_set_next_attempt |
| [Prev](extending.hooks.core.ec_message_enqueue.php)  | Chapter 18. Hooks in the core scope |  [Next](extending.hooks.core.ec_ssl_SSL_CTX_fixup.php) |

<a name="extending.hooks.core.ec_message_set_next_attempt"></a>
## Name

ec_message_set_next_attempt

## Synopsis

`#include "hooks/core/ec_message_set_next_attempt.h"`

| `int **ec_message_set_next_attempt**(` | <var class="pdparam">closure</var>, |   |
|   | <var class="pdparam">am</var>, |   |
|   | <var class="pdparam">now</var>, |   |
|   | <var class="pdparam">rv</var>`)`; |   |

`void * <var class="pdparam">closure</var>`;
`ec_message * <var class="pdparam">am</var>`;
`struct timeval * <var class="pdparam">now</var>`;
`int * <var class="pdparam">rv</var>`;

| `int **has_core_ec_message_set_next_attempt_hook**(` | `)`; |   |

| `void **register_core_ec_message_set_next_attempt_hook_first**(` | <var class="pdparam">hook</var>, |   |
|   | <var class="pdparam">closure</var>`)`; |   |

`ec_hook_core_ec_message_set_next_attempt_func_t <var class="pdparam">hook</var>`;
`void *<var class="pdparam">closure</var>`;

| `void **register_core_ec_message_set_next_attempt_hook_last**(` | <var class="pdparam">hook</var>, |   |
|   | <var class="pdparam">closure</var>`)`; |   |

`ec_hook_core_ec_message_set_next_attempt_func_t <var class="pdparam">hook</var>`;
`void *<var class="pdparam">closure</var>`;

| `int **call_core_ec_message_set_next_attempt_hook**(` | <var class="pdparam">am</var>, |   |
|   | <var class="pdparam">now</var>, |   |
|   | <var class="pdparam">rv</var>`)`; |   |

`ec_message * <var class="pdparam">am</var>`;
`struct timeval * <var class="pdparam">now</var>`;
`int * <var class="pdparam">rv</var>`;<a name="idp21098560"></a>
## Description

The `ec_message_set_next_attempt` hook allows modules to set the next attempt time of a message. If you decide to take no action (and want the default behavior), return 0\. If you set the expiration time, return 1, and set *`rv`* to 1 to indicate success, 0 to indicate failure.

| [Prev](extending.hooks.core.ec_message_enqueue.php)  | [Up](extending.hooks.core.php) |  [Next](extending.hooks.core.ec_ssl_SSL_CTX_fixup.php) |
| ec_message_enqueue  | [Table of Contents](index.php) |  ec_ssl_SSL_CTX_fixup |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)