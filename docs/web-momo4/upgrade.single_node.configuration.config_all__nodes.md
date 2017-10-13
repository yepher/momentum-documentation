| 10.4. Configuration Changes |
| [Prev](upgrade.single_node.configuration.flyway.php)  | Chapter 10. Upgrade - Single Node |  [Next](upgrade.single_node.configuration.software_upgrade.php) |

## 10.4. Configuration Changes

Update the following files by copying the root -> application -> vertica stanza to root -> vertica:

*   `/opt/msys/app/metrics-api/config/production.json`

*   `/opt/msys/app/webhooks-api/config/production.json`

### Note

In the webhooks-api version, a Cassandra stanza follows the Application stanza, so you will need to add a comma to the Vertica sub-stanza getting moved. This will help preserve the proper json formatting.

1.  Open a file editor.

    ```
    % shopt -s extglob
    vim -o /opt/msys/app/+(metrics|webhooks)-api/config/production.json /opt/msys/app/metrics-etl/config/production.json
    ```

2.  Configure the `/opt/msys/app/<metrics and webhooks>-api/config/production.json` file.

    ```
    {
      "application":{
        "vertica": {  //from here
            // stuff, probably hosts
        } //to here
      },

      //put it here
      "vertica": {
         // stuff, probably hosts
      }
    }
    ```

3.  Update or verify the `/opt/msys/app/metrics-etl/config/production.json` file by copying the root -> application -> vertica stanza to root -> vertica.

    ```
    {
      "application":{
        "vertica": {  //from here
            // stuff, probably hosts
        } //to here
      },

      //put it here
      "vertica": {
         // stuff, probably hosts
      }
    ```

| [Prev](upgrade.single_node.configuration.flyway.php)  | [Up](upgrade.single_node.php) |  [Next](upgrade.single_node.configuration.software_upgrade.php) |
| 10.3. Prepare and Run Flyway  | [Table of Contents](index.php) |  10.5. Software Upgrade |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)