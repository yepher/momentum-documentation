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

| async_bounce_rendering |
| [Prev](conf.ref.allow_trailing_whitespace_in_commands.php)  | 9.2. Configuration Files and Option Details |  [Next](conf.ref.authorization.php) |

<a name="conf.ref.async_bounce_rendering"></a>
## Name

async_bounce_rendering — which thread pool to use for bounce rendering

## Synopsis

`Async_Bounce_Rendering = true`

<a name="idp7509424"></a>
## Description

When a message fails to be delivered due to a timeout, a 5XX error from the remote MTA or a `reject` or `ec_reject` in a Sieve script, Momentum generates and injects a bounce message. If async_bounce_rendering is true, this job is done in the IO thread pool, otherwise it gets done in the scheduler before returning control to the code that noted the bounce, namely the outbound SMTP, the Sieve script or the mail queue maintainer.

The default value for this option is `true`.

<a name="idp7513248"></a>
## Scope

Async_Bounce_Rendering is valid in the global scope.

<a name="idp7514896"></a>
## See Also

[reject](sieve.ref.reject.php "reject")

| [Prev](conf.ref.allow_trailing_whitespace_in_commands.php)  | [Up](conf.ref.files.php) |  [Next](conf.ref.authorization.php) |
| allow_trailing_whitespace_in_commands  | [Table of Contents](index.php) |  authorization |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)