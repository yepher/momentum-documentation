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

| D.14. The TIME Errors |
| [Prev](START-panic-log-errors.php)  | Appendix D. Panic Log Errors |  [Next](responses.php) |

## D.14. The TIME Errors

In this section errors are sorted by severity.

<a name="TIME-table-panic-log-errors"></a>

**Table D.14. TIME errors**

| Error Level | Facility | Error Message | Action |
| --- | --- | --- | --- |
| DERROR | TIME | CreateWaitableTimer failed *`LastError`* **Platform: Windows**  | An internal error occurred. Contact support if it persists. |
| DERROR | TIME | SetWaitableTimer failed *`LastError`* **Platform: Windows**  | An internal error occurred. Contact support if it persists. |
| DERROR | TIME | WaitForSingleObject failed *`GetLastError`* **Platform: Windows**  | An internal error occurred. Contact support if it persists. |

| [Prev](START-panic-log-errors.php)  | [Up](error-messages.php) |  [Next](responses.php) |
| D.13. The START Errors  | [Table of Contents](index.php) |  Appendix E. Message Responses |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)