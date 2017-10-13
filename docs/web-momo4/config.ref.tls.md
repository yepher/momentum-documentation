| tls |
| [Prev](conf.ref.timestampformat.php)  | Chapter 72. Configuration Options Reference |  [Next](config.tls_allow_renegotiation.php) |

<a name="config.ref.tls"></a>
## Name

tls — determine whether to use TLS connection for outbound mail

## Synopsis

`TLS = "no|ifavailable|required"`

<a name="idp26890704"></a>
## Description

**Configuration Change. ** Support for opportunistic TLS is available as of version 4.1.

This option determines whether or not Transport Layer Security should be used when delivering email. Note that this does not guarantee end-to-end security but only that of the first hop from the MTA.

This option can be set to the following:

*   `no` – Disables the negotiation of TLS for outbound deliveries regardless of whether it is available.

*   `ifavailable` – Enables opportunistic TLS. If the remote mail exchange supports TLS and the TLS negotiation succeeds, the mail will be delivered over TLS.

    *   For version 4.0 – If the negotiation fails, the message is put back into the delayed queue and retried later.

    *   For version 4.1 and later – If the negotiation fails, the value of the TLS_Ifavailable_fallback option determines the behavior, which defaults to Momentum immediately trying to send the message as plain-text.

*   `required` – Disables the sending of mail unless a successful TLS negotiation takes place with the remote mail exchange.

The default value is `no`.

<a name="idp26903056"></a>
## Scope

`tls` is valid in the binding, binding_group, domain, and global scopes.

| [Prev](conf.ref.timestampformat.php)  | [Up](config.options.ref.php) |  [Next](config.tls_allow_renegotiation.php) |
| timestampformat  | [Table of Contents](index.php) |  tls_allow_renegotiation |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)