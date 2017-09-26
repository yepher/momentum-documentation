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

| control_pre_command |
| [Prev](extending.hooks.core.control_post_control.php)  | Chapter 18. Hooks in the core scope |  [Next](extending.hooks.core.control_pre_control.php) |

<a name="extending.hooks.core.control_pre_command"></a>
## Name

control_pre_command

## Synopsis

`#include "hooks/core/control_pre_command.h"`

| `int **control_pre_command**(` | <var class="pdparam">closure</var>, |   |
|   | <var class="pdparam">cc</var>, |   |
|   | <var class="pdparam">response</var>`)`; |   |

`void * <var class="pdparam">closure</var>`;
`command_construct * <var class="pdparam">cc</var>`;
`string * <var class="pdparam">response</var>`;

| `int **has_core_control_pre_command_hook**(` | `)`; |   |

| `void **register_core_control_pre_command_hook_first**(` | <var class="pdparam">hook</var>, |   |
|   | <var class="pdparam">closure</var>`)`; |   |

`ec_hook_core_control_pre_command_func_t <var class="pdparam">hook</var>`;
`void *<var class="pdparam">closure</var>`;

| `void **register_core_control_pre_command_hook_last**(` | <var class="pdparam">hook</var>, |   |
|   | <var class="pdparam">closure</var>`)`; |   |

`ec_hook_core_control_pre_command_func_t <var class="pdparam">hook</var>`;
`void *<var class="pdparam">closure</var>`;

| `int **call_core_control_pre_command_hook**(` | <var class="pdparam">cc</var>, |   |
|   | <var class="pdparam">response</var>`)`; |   |

`command_construct * <var class="pdparam">cc</var>`;
`string * <var class="pdparam">response</var>`;<a name="idp20868784"></a>
## Description

Given *`cc`*, hooks registered here can perform tasks prior to the built-in console commands, or even bypass the built-in commands completely. Return 1 to skip the default command behaviour; any additional pre_command hooks will also be skipped. Return 0 to allow the default command behaviour (and any other pre_command hooks) to continue. *`response`* is provided for output handed back to the console client.

| [Prev](extending.hooks.core.control_post_control.php)  | [Up](extending.hooks.core.php) |  [Next](extending.hooks.core.control_pre_control.php) |
| control_post_control  | [Table of Contents](index.php) |  control_pre_control |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)