| cluster_outbound_throttle_messages |
| [Prev](conf.ref.cluster_outbound_throttle_connections.php)  | Chapter 72. Configuration Options Reference |  [Next](conf.ref.cluster_scope_max_outbound_connections.php) |

<a name="conf.ref.cluster_outbound_throttle_messages"></a>
## Name

cluster_outbound_throttle_messages — limit the rate at which messages are delivered, and enforce it across the cluster

## Synopsis

`Cluster_Outbound_Throttle_Messages = "1"`

`Cluster_Outbound_Throttle_Messages = "1/60"`

<a name="idp23960688"></a>
## Description

This allows you to limit the rate at which Momentum will attempt to deliver mail. It can be employed to globally limit throughput or to reduce the rate sent to a particular domain.

If a single integer parameter is provided, Momentum will ensure that no more than the specified number of messages are sent in a given second of time. If a proper fraction parameter is provided, Momentum will limit the number of sent message to the number specified in the numerator over the time window in seconds specified by the denominator.

### Note

For best results, a throttle in the same scope and with the same values should also be defined using [cluster_outbound_throttle_connections](conf.ref.cluster_outbound_throttle_connections.php "cluster_outbound_throttle_connections")

The cluster module must be configured with the outbound throttle parameters.

<a name="idp23966000"></a>
## Scope

`cluster_outbound_throttle_messages` is valid in the binding_group, domain, and global scopes.

| [Prev](conf.ref.cluster_outbound_throttle_connections.php)  | [Up](config.options.ref.php) |  [Next](conf.ref.cluster_scope_max_outbound_connections.php) |
| cluster_outbound_throttle_connections  | [Table of Contents](index.php) |  cluster_scope_max_outbound_connections |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)