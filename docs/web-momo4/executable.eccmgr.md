| eccmgr |
| [Prev](executable.eccfg.php)  | Chapter 74. Executable Commands Reference |  [Next](executable.eccmgr_ctl.php) |

<a name="executable.eccmgr"></a>
## Name

eccmgr — Momentum Cluster Manager

## Synopsis

`/opt/msys/ecelerity/sbin/eccmgr` [ -c *`configfile`* ] [ -g *`group`* ] [ -n ] [ -v ] [ -e ] [ -d ] [ -V ]

<a name="idp12173616"></a>
## Description

**eccmgr** is the Momentum Cluster Manager. On start up, the script **/etc/init.d/eccmgr start**       runs **eccmgr** as a service on the node designated as cluster manager.

Use **eccmgr_ctl** to start, stop, or restart this process.

The behavior of the Momentum Cluster Manager is configured in `eccluster.conf`.

The following options are available:

<dl class="variablelist">

<dt>-c configfile</dt>

<dd>

Use an alternate config file.

</dd>

<dt>-g *`group`*</dt>

<dd>

Specify the cluster group.

</dd>

<dt>-n</dt>

<dd>

Skip locking (flock) files (**NOT RECOMMENDED** ).

</dd>

<dt>-v</dt>

<dd>

Verbose mode. This option can be used up to four times for increasing levels of verbosity.

</dd>

<dt>-e</dt>

<dd>

Set alternate extensions directory.

</dd>

<dt>-d</dt>

<dd>

Run in the foreground, leave stdout, stderr open.

</dd>

<dt>-V</dt>

<dd>

Show version information.

</dd>

</dl>

<a name="idp12193728"></a>
## See Also

[eccmgr_ctl](executable.eccmgr_ctl.php "eccmgr_ctl"), [Section 16.2, “`eccluster.conf` File”](conf.ref.eccluster.conf.php "16.2. eccluster.conf File"), [Chapter 38, *Using the Cluster Manager (**eccmgr**)*](cluster.config.operations.php "Chapter 38. Using the Cluster Manager (eccmgr)") 

| [Prev](executable.eccfg.php)  | [Up](exec.cmds.ref.php) |  [Next](executable.eccmgr_ctl.php) |
| eccfg  | [Table of Contents](index.php) |  eccmgr_ctl |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)