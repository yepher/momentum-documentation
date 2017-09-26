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

| ecelerity |
| [Prev](executable.ecconfigd_ctl.php)  | Chapter 74. Executable Commands Reference |  [Next](executable.jlog_change_endian.php) |

<a name="executable.ecelerity"></a>
## Name

ecelerity — Momentum Application Server

## Synopsis

`/opt/msys/ecelerity/sbin/ecelerity` [ -c *`configfile`* ] [ -d ] [ -h ] [ -n *`service`* ] [ -s ]

<a name="idp11899792"></a>
## Description

**ecelerity** is the main server component of the Momentum Application Server. On start up, the script **/etc/init.d/ecelerity start**       starts Momentum.

Use **ec_ctl** to start, stop, or restart this process. This ensures that environment variables are set and that startup scripts are run.

The `ecelerity.conf` file is the master configuration file for **ecelerity**.

While the recommended method for starting Momentum is to use **ec_ctl**, you may also launch Momentum from the command line. The following options are available:

<dl class="variablelist">

<dt>-h</dt>

<dd>

Display a help message, showing all command line options.

</dd>

<dt>-d</dt>

<dd>

Run in the foreground, leave stdout, stderr open.

### Note

The configuration system has a search path algorithm, and the first element in the path it searches is ‘`.`.’. This means that if you run ecelerity in the foreground, you may get different results than if you run it in the background (because when running in the background, the start scripts set the working directory for the process to ‘`/`’).

To make sure you're chasing down the right error, make sure you always do a **`cd /`**    before running ecelerity in the foreground. Doing so makes the environment the same as when running in the background, and consequently the errors will be the same.

In a cluster configuration, do not invoke this command from within the **eccmgr** service.

</dd>

<dt>-n *`service`*</dt>

<dd>

Skip service offering. Service can be 'esmtp', 'ecstream', or 'queue'.

</dd>

<dt>-c *`configfile`*</dt>

<dd>

Use an alternate config file.

</dd>

</dl>

<a name="idp13199456"></a>
## See Also

[ec_ctl](executable.ec_ctl.php "ec_ctl"), [Section 15.6, “`ecelerity.conf` File”](conf.ref.ecelerity.conf.php "15.6. ecelerity.conf File"), [Chapter 36, *Starting Momentum (**ecelerity**)*](conf.starting.php "Chapter 36. Starting Momentum (ecelerity)") 

| [Prev](executable.ecconfigd_ctl.php)  | [Up](exec.cmds.ref.php) |  [Next](executable.jlog_change_endian.php) |
| ecconfigd_ctl  | [Table of Contents](index.php) |  jlog_change_endian |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)