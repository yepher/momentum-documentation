| msys.pcre.match |
| [Prev](lua.ref.msys.gcm.gcm_get_result_error_code.php)  | Chapter 70. Lua Functions Reference |  [Next](lua.ref.msys.pcre.replace.php) |

<a name="lua.ref.msys.pcre.match"></a>
## Name

msys.pcre.match — Perform a PCRE regex match operation

<a name="idp18230080"></a>
## Synopsis

`msys.pcre.match(subject, pattern);`

```
subject: string
pattern: string
```
<a name="idp18233072"></a>
## Description

Perform a PCRE regex match operation. Captures return their matches in numeric order and are referenced using the numeric index preceded by a dollar sign. The first capture is referenced using `$1`, the second using `$2` and so on. Pass in the string to be matched and the PCRE regex pattern to match against.

Enable this function with the statement `require('msys.pcre')`.

This function returns three values:

`matches, errstr, errnum = msys.pcre.match(subject, pattern);`

The return values are as follows:

*   `matches` nil if no matches were found, otherwise a table consisting of the following indices:

    *   `0` complete matched portion of the string

    *   `1` the first capture subexpression

    *   `2` the second capture subexpression

    *   `...` additional capture subexpression

    If named captures, (?P<name>....), were used in the pattern, then the names will be also be keys in the table, with their values set to the value of the appropriate subexpression.

*   `errstr` if there was a failure during compilation of the regex, this string will contain the error message

*   `errnum` this will contain a numeric representation of the error condition

<a name="idp18250160"></a>
## See Also

[msys.pcre.split](lua.ref.msys.pcre.split.php "msys.pcre.split"), [msys.pcre.replace](lua.ref.msys.pcre.replace.php "msys.pcre.replace")

| [Prev](lua.ref.msys.gcm.gcm_get_result_error_code.php)  | [Up](lua.function.details.php) |  [Next](lua.ref.msys.pcre.replace.php) |
| msys.gcm.gcm_get_result_error_code  | [Table of Contents](index.php) |  msys.pcre.replace |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)