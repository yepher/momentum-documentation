| doc:xpath |
| [Prev](lua.ref.xml.doc_tostring.php)  | Chapter 70. Lua Functions Reference |  [Next](lua.ref.xml.node_addchild.php) |

<a name="lua.ref.xml.doc_xpath"></a>
## Name

doc:xpath — Perform an XPath query

<a name="idp19374208"></a>
## Synopsis

`require('xml');`

`doc:xpath(query, [contextnode]);`

```
query: string
contextnode: string (optional)
```
<a name="idp19377936"></a>
## Description

This function performs an XPath query and returns an iterator over the resultant set of nodes. You may specify an optional node from the same document to use as context for the XPath query. *Note*: If you include a context node you must enclose it in square brackets.

<a name="lua.ref.xml.doc_xpath.example"></a>

**Example 70.75. doc:xpath example**

```
...
for node in doc:xpath("//item") do
  print(node:name())
end
```

<a name="idp19382416"></a>
### See Also

[xml.parsexml](lua.ref.xml.parsexml.php "xml.parsexml")

| [Prev](lua.ref.xml.doc_tostring.php)  | [Up](lua.function.details.php) |  [Next](lua.ref.xml.node_addchild.php) |
| doc:tostring  | [Table of Contents](index.php) |  node:addchild |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)