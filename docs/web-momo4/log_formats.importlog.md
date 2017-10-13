| 35.6. `importlog` |
| [Prev](log_formats.httplog.php)  | Chapter 35. Log Formats |  [Next](log_formats.mainlog.php) |

## 35.6. `importlog`

The `importlog` records the outcome of a [spool import](console_commands.spool_import.php "spool import") operation. It is configured in the [ec_logger](modules.ec_logger.php "71.30. EC_logger – Momentum-Style Logging").

### 35.6.1. Import Records

The following is a description of the fields:

<a name="log_formats.import_logger.fields"></a>

**Table 35.8. Import Record Fields**

| Offset | Example Field | Description |
| --- | --- | --- |
| 0 | 1064869327 | Date of the event in Unix timestamp format (seconds since 00:00:00 Jan 1, 1970) |
| 1 | 00/00-25004-31B987F3 | 

Message's original in-spool message-id

(This is a unique value per message and corresponds with its location in the spool being imported.)

 |
| 2 | I | `I` indicates that this log line is an import event. |
| 3 | 00/00-25004-31B987F3 | 

Message's new in-spool message-id

(This is usually the same as the message-id recorded in field 1, but may be altered during import to avoid collisions with existing messages with the same identifier.)

 |
| 4 | 1 | 

Result indicator

(This is a number between 1 and 4 with the following meanings: 1 is complete success, 2 indicates failure during the read of metadata, 3 is failure reading the message from the spool. and 4 is failure writing the message into the main Momentum spool.)

 |
| 5 | /var/spool/my-alternative-spool | Base directory containing the spool being imported |

| [Prev](log_formats.httplog.php)  | [Up](log_formats.php) |  [Next](log_formats.mainlog.php) |
| 35.5. `httplog`  | [Table of Contents](index.php) |  35.7. `mainlog` |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)