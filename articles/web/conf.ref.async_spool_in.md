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

| async_spool_in |
| [Prev](conf.ref.async_close_concurrency.php)  | 9.2. Configuration Files and Option Details |  [Next](conf.ref.async_swap_in.php) |

<a name="conf.ref.async_spool_in"></a>
## Name

async_spool_in — number of threads to use for spooling from disk

## Synopsis

`async_spool_in = 1`

<a name="idp4177488"></a>
## Description

During startup, the metadata for messages in the spool needs to be spooled in so that Momentum can construct its in-memory representation of the spool. The `async_spool_in` specifies how many threads should be spawned to read in that information. Once the entire spool has been processed, the spool in threads will terminate.

The default value for this option is 1 thread.

### Note

This option is deprecated starting with Momentum 2.2 in favor of the more flexible `ThreadPool` stanza. See [threadpool](conf.ref.threadpool.php "threadpool") for more information. As of version 3.0, this option is no longer available.

<a name="idp4182640"></a>
## Scope

async_spool_in is valid in the global scope.

<a name="idp4184256"></a>
## See Also

[async_swap_in](conf.ref.async_swap_in.php "async_swap_in")

| [Prev](conf.ref.async_close_concurrency.php)  | [Up](conf.ref.files.php) |  [Next](conf.ref.async_swap_in.php) |
| async_close_concurrency  | [Table of Contents](index.php) |  async_swap_in |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)