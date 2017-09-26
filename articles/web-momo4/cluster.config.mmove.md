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

| 27.2. `duravip_follow` and the #mmove Binding |
| [Prev](cluster.config.duravip.php)  | Chapter 27. DuraVIP™: IP Fail over |  [Next](cluster.config.arp_all_hosts.php) |

## 27.2. `duravip_follow` and the #mmove Binding

The #mmove binding is the cluster message movement binding in the default binding group. This is a virtual binding for moving messages between nodes.

The current design of Momentum assumes that #mmove traffic will be the exception, rather than the rule. If you are seeing a lot of traffic on the #mmove binding, this is an indication of an underlying problem with the way the traffic is being injected. It will always be less efficient to inject to one node, #mmove to another node, and then deliver from that node. It is always more efficient to inject directly to the delivery node.

Sometimes a client doesn't know until the message is injected which binding to assign it to, but often this is known beforehand. When you do know which binding a message will be assigned to, it is best practice to associate a specific Listener IP with a specific binding (or binding group) by using `Duravip_Follow` in the Listener stanza. Injecting to a given Listener means that the outbound binding is always local. The alternative is to always inject to binding groups and have each binding group contain a preferred binding on each node, so that delivery is always local.

If you wish to determine the amount of traffic on the #mmove binding, use the [mailq](console_commands.mailq.php "mailq") command from the system console.

### ECmmove2

ECmmove2 is the service that handles DuraVIP™ message moves. A node will connect to the ECCluster_listener and indicate that it is going to initiate an mmove; the connection is then passed over to the SMTP state machines on both sides and completes using regular SMTP.

| [Prev](cluster.config.duravip.php)  | [Up](cluster.config.duravip.php) |  [Next](cluster.config.arp_all_hosts.php) |
| Chapter 27. DuraVIP™: IP Fail over  | [Table of Contents](index.php) |  27.3. Address Resolution Protocol (ARP) traffic |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)