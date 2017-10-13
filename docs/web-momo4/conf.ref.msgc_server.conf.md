| 16.4. `msgc_server.conf` File |
| [Prev](conf.ref.ecelerity_cluster.conf.php)  | Chapter 16. Cluster-specific Configuration |  [Next](cluster.listeners.php) |

## 16.4. `msgc_server.conf` File

The `msgc_server.conf` file contains the configuration relevant to the cluster messaging bus. This file is referenced from the `eccluster.conf` file on the cluster manager and from the `ecelerity-cluster.conf` file on nodes. It MUST live in the global portion of the repository, as it must be the same for all nodes in the cluster.

### Note

Restart [Section 15.1.3, “Configuration Management (**ecconfigd**)”](conf.overview.php#conf.ecconfigd "15.1.3. Configuration Management (ecconfigd)") after making extensive changes to `msgc_server.conf`, such as adding multiple nodes. Use the command **`/etc/init.d/ecconfigd restart`**         .

For a discussion of scopes and fallbacks, see [Section 15.3, “Configuration Scopes and Fallback”](ecelerity.conf.fallback.php "15.3. Configuration Scopes and Fallback").

For a summary of all the non-module specific configuration options, refer to [Chapter 66, *Configuration Options Summary*](config.options.summary.php "Chapter 66. Configuration Options Summary") .

Modules and their configuration options are discussed in the [Chapter 71, *Modules Reference*](modules.php "Chapter 71. Modules Reference") .

The following are the modules configured in the `msgc_server.conf` file:

<dl class="variablelist">

<dt>msgc_server</dt>

<dd>

The msgc_server module maintains connections with all other msgc_servers in the network (if they exist).

</dd>

<dt>msgc_client</dt>

<dd>

The msgc_client module connects to msgc_server in order to participate in the cluster.

</dd>

<dt>msgcserver_listener</dt>

<dd>

The msgcserver_listener mediates between msgc_servers and between msgc_servers and their clients. See [Section 16.5.2, “Msgcserver_Listener Configuration”](cluster.listeners.php#msgcserver_listener "16.5.2. Msgcserver_Listener Configuration").

</dd>

</dl>

| [Prev](conf.ref.ecelerity_cluster.conf.php)  | [Up](cluster.php) |  [Next](cluster.listeners.php) |
| 16.3. `ecelerity-cluster.conf` File  | [Table of Contents](index.php) |  16.5. Cluster-specific Listeners |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)