| write config |
| [Prev](console_commands.version.php)  | Chapter 73. Non-Module-Specific Console Commands |  [Next](exec.cmds.ref.php) |

<a name="console_commands.write_config"></a>
## Name

write config — display current running configuration

## Synopsis

write config *`/path/to/file`*

<a name="idp13149488"></a>
## Description

Instruct Momentum to display the current running configuration over the console. If a file name is passed as a parameter, Momentum will open and write the configuration to that file on the server running Momentum, **not necessarily the machine from which you are running ec_console** .

To write the current settings to file, issue the command **write config `/var/tmp/ecelerity.new.config`**                                        being sure to choose a directory where you have write permission.

### Warning

Overwriting your existing `ecelerity.conf` file is not recommended. Note that files "included" in your configuration file will **not** be copied. If you wish to make permanent changes to your configuration file, edit the file directly.

If you are in the middle of a transaction (begun with **config begin** ) **write config**        will not show any changes you have made. Use **config showrecurse**             or **config show**      instead. For more information see [config](console_commands.config.php "config").

| [Prev](console_commands.version.php)  | [Up](console.cmds.ref.php) |  [Next](exec.cmds.ref.php) |
| version  | [Table of Contents](index.php) |  Chapter 74. Executable Commands Reference |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)