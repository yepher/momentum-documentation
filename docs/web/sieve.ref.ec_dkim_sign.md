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

| ec_dkim_sign |
| [Prev](sieve.ref.ec_dkim_responsible_domain.php)  | Chapter 15. Sieve++ Function Reference |  [Next](sieve.ref.ec_dns_lookup.php) |

<a name="sieve.ref.ec_dkim_sign"></a>
## Name

ec_dkim_sign — Sign a message with the DKIM protocol

## Synopsis

`ec_dkim_sign` [ *`parameters_hash`* ]

<a name="idp14080272"></a>
## Description

`ec_dkim_sign` signs the current message with a DKIM signature. By default it uses the configured parameters on the DKIM module configuration stanza. If desired, a hash table of parameter overrides may be passed as the only argument to the Sieve extension. It may contain the following parameters:

### Note

This feature requires the DKIM module. See [Section 14.22, “dkim – DomainKeys Identified Mail Signatures”](modules.dkim.php "14.22. dkim – DomainKeys Identified Mail Signatures") for more information.

**Configuration Change. ** This feature is available starting from Momentum 2.2.

<dl class="variablelist">

<dt>base_domain/signing_domain</dt>

<dd>

Override the default signing domain. These two parameters are synonyms for one another, each will have the same effect.

</dd>

<dt>header_canon</dt>

<dd>

Override the default header canonicalization setting.

</dd>

<dt>body_canon</dt>

<dd>

Override the default body canonicalization setting.

</dd>

<dt>digest</dt>

<dd>

Override the default digest setting.

</dd>

<dt>headerlist</dt>

<dd>

Override the default list of headers to sign.

</dd>

<dt>identity</dt>

<dd>

Override the default signing identity.

</dd>

<dt>selector</dt>

<dd>

Override the default signing selector.

</dd>

<dt>keyfile</dt>

<dd>

Override the default signing key file, which may be parameterized as defined in the [Section 14.22, “dkim – DomainKeys Identified Mail Signatures”](modules.dkim.php "14.22. dkim – DomainKeys Identified Mail Signatures") configuration documentation.

</dd>

<dt>keybuf</dt>

<dd>

Override the default signing key. This hash entry must contain the PEM encoded private key to use for signing the messages. This must be a contiguous string, with no line breaks and no white space, without the --BEGIN and --END tags that are found in the key file itself. The format is similar to the format used to store the public key in the DKIM DNS records.

</dd>

<dt>body_length_limit</dt>

<dd>

Override the default body_length_limit setting.

</dd>

<dt>lifetime</dt>

<dd>

**Configuration Change. ** This feature is available as of version 2.2.3.46.

Override the default lifetime setting.

</dd>

</dl>

The `core_final_validation` hook is triggered from the SWAPOUT pool as the last step before journaling the message to spool. Because you are guaranteed that nothing will change the message contents, it is best to execute `ec_dkim_sign` in the `core_final_validation` hook. This is important because message modifications that occur after a signature is computed will render the signature invalid. This hook point must run synchronously; doing otherwise will lead to undefined behavior.

### Warning

While it is possible to use this function in the data phase, doing so will have a massive impact on performance, as the system would be occupied with signing instead of processing mail, and the throughput would suffer tremendously. However, there can only be one Sieve script bound to the core_final_validation hook. If you want to sign both DKIM and DomainKeys, put your code into the same file.

Set the sieve `async` option to `false` when using the core_final_validation_hook otherwise you may experience spool corruption.

Sieve scripts implementing the core_final_validation hook should not modify the message since it may have already been written to the spool.

Find a sample sieve configuration below:

```
Validate validate/sieve sieve {
  hook:core_final_validation [
    script = "/path/to/dkim_sign_script.siv"
    async = "false"
  ]
}
```

Documentation for how to execute a Sieve script at a hook point can be found on the [Section 14.51, “sieve – The Sieve Module”](modules.sieve.php "14.51. sieve – The Sieve Module") documentation page.

<a name="example.ec_dkim_sign"></a>

**Example 15.38. ec_dkim_sign example**

```
$params = hash_create;
hash_set $params "selector" "myselector";
hash_set $params "signing_domain" "my.signing.domain.com";
ec_dkim_sign $params;
```

| [Prev](sieve.ref.ec_dkim_responsible_domain.php)  | [Up](sieve.ref.php) |  [Next](sieve.ref.ec_dns_lookup.php) |
| ec_dkim_responsible_domain  | [Table of Contents](index.php) |  ec_dns_lookup |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)