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

| 14.47. response_transcode – Module |
| [Prev](modules.regex_binding2.php)  | Chapter 14. Modules Reference |  [Next](modules.sched.php) |

## 14.47. response_transcode – Module

<a class="indexterm" name="idp12666096"></a>

**Configuration Change. ** This feature is available starting from Momentum 2.2.2.38.

The response_transcode module can be used to work around broken remote servers that send incorrect response codes. For example, with this module you can change a hard bounce to a soft bounce, enabling you to log the bounce in order to later resend the message.

### Warning

Since it is possible to rewrite permanent errors as temporary errors, use this module carefully. Resubmitting mail that a remote server has already rejected with a permanent error can be seen as a hostile action.

### 14.47.1. Configuration

<a name="example.response_transcode"></a>

**Example 14.64. response_transcode module**

```
Module generic/response_transcode response_transcode {
}
```

### Note

You can transcode "[internal]" transient failures but you cannot transcode "[internal]" permanent failures. For a listing of "[internal]" failures see [Appendix E, *Message Responses*](responses.php "Appendix E. Message Responses") .

The module defines two options, Response_Transcode_Pattern and Response_Transcode_Replace. For more information about these options see [response_transcode_replace](conf.ref.response_transcode_replace.php "response_transcode_replace") and [response_transcode_pattern](conf.ref.response_transcode_pattern.php "response_transcode_pattern").

| [Prev](modules.regex_binding2.php)  | [Up](modules.php) |  [Next](modules.sched.php) |
| 14.46. regex_binding2 – Regular Expression Based Bindings (II)  | [Table of Contents](index.php) |  14.48. sched – The Schedule Module |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)