| [Prev](lua.ref.msg_text_match)  | Chapter 70. Lua Functions Reference |  [Next](lua.ref.msgpart_addFirstChild) |

<a name="lua.ref.msg_text_replace"></a>
## Name

msg:text_replace — Streaming interface to a PCRE replacement of textual content from the message body

<a name="idp17001888"></a>
## Synopsis

`msg:text_replace(pattern, replacement);`

```
pattern: string
replacement: string
```
<a name="idp17004832"></a>
## Description

Streaming interface to a PCRE replacement of textual content from the message body. Only parts that have a 'text' mime type will be included in the search. Text parts will be iterated, transfer decoded and converted to UTF-8\. If a replacement is made, the revised text is converted back to the original charset for that part and the original transfer encoding applied, except in the case where the content was originally 7-bit clean and had no transfer encoding: if the replacement content is not 7-bit clean, transfer encoding will be added.

Enable this function with the statement `require('msys.extended.message');`.

| [Prev](lua.ref.msg_text_match)  | [Up](lua.function.details) |  [Next](lua.ref.msgpart_addFirstChild) |
| msg:text_match  | [Table of Contents](index) |  msgpart:addFirstChild |

