| 71.5. alias – Alias Expansion |
| [Prev](modules.alerting.php)  | Chapter 71. Modules Reference |  [Next](modules.antivirus.php) |

## 71.5. alias – Alias Expansion

<a class="indexterm" name="idp19680880"></a>

The alias module lets you rewrite the recipient addresses of messages passing through Momentum. It is similar in spirit to sendmail's `/etc/aliases`, but alias expansions can be stored in any backend supported by Momentum's datasource layer. [Section 71.29, “ds_core - Datasource Query Core”](modules.ds_core.php "71.29. ds_core - Datasource Query Core")

When the alias module is loaded, alias expansion is disabled by default. The `Alias_Schemes` option, a list that can be specified in the Domain or Global scopes, enables the list of schemes that will be used to expand recipient addresses in that domain in decreasing order of preference. Expansion of a recipient address stops after the first alias scheme that yields a non-empty expansion for that address; the original address is replaced in the recipient list by the address(es) in the expansion. To prevent loops, a recipient address that has been expanded cannot be added back to the list of recipients as the result of expanding another recipient address.

### 71.5.1. Configuration

A Scheme is specified in an alias module. The mandatory `cache` parameter specifies the datasource cache that will be used as the backend, in this example `aliasdb`. The mandatory `query` parameter specifies the query string that will be used. The `map` dictionary specifies the alias map used to construct the bind variables used together with the query string; though technically optional, it is almost certainly necessary. The optional `column` parameter specifies the name of the column containing the results of the expansion; it may be omitted if the query only returns a single column. All the values (if any) in the results column must be valid email addresses.

```
alias "alias1" {
  Scheme "myscheme" {
    query = "SELECT expansion FROM foo WHERE address = :address"
    cache = "aliasdb"
    map = [
        address = "%{rcptto}"
      ]
  }
}
Datasource "aliasdb" {
  uri = ( "sqlite:/path/to/sqlite.db" )
}
Domain "example.com" {
  Alias_Schemes = ( "myscheme" )
}
```

A map dictionary is specified by the `map` option. It may contain any number of arbitrarily named variables; macro expansion is performed on these, with the substrings `%{localpart}`, `%{domain}` and `%{rcptto}` being replaced by the local part, domain and complete address of the recipient being expanded, respectively. No other substrings of the form `%{...}` are allowed.

Within the desired domain, the `Alias_Schemes` option is set to the Scheme name defined within the alias module.

### 71.5.2. See Also

[alias_schemes](conf.ref.alias_schemes.php "alias_schemes") and [Section 71.29, “ds_core - Datasource Query Core”](modules.ds_core.php "71.29. ds_core - Datasource Query Core").

| [Prev](modules.alerting.php)  | [Up](modules.php) |  [Next](modules.antivirus.php) |
| 71.4. alerting – Send Alerting Emails  | [Table of Contents](index.php) |  71.6. antivirus – Antivirus |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)