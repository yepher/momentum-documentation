| Chapter 5. Hardware Considerations |
| [Prev](p.installing.php)  | Part II. Installing Momentum |  [Next](hardware.config_options.php) |

## Chapter 5. Hardware Considerations

**Table of Contents**

<dl class="toc">

<dt>[5.1\. Server Roles](hardware.requirements.php#hardware.server_roles)</dt>

<dt>[5.2\. Configuration Options](hardware.config_options.php)</dt>

<dt>[5.3\. Hardware Scaling Approach](hardware.scaling.php)</dt>

<dt>[5.4\. Environmental Considerations](hardware.environmental.php)</dt>

<dt>[5.5\. Hardware Deployment Configuration](hardware.config.php)</dt>

<dt>[5.6\. Production Environment Configurations](production.config.php)</dt>

<dt>[5.7\. Additional Configuration Notes](addl.config.notes.php)</dt>

</dl>

The Momentum platform is designed to deliver high volumes of messaging traffic. This is accomplished through architecture that can be scaled vertically on all nodes and horizontally by adding nodes. When planning a Momentum deployment, you must understand both the physical hardware and the deployment environment. This section will help you determine the best deployment for the volumes you need to support, as well as the correct hardware for your current configuration and for expected growth.

## 5.1. Server Roles

Momentum is deployed as several distinct “roles”, each providing different functionality of the Momentum Solution. The available roles are:

*   Platform Role

    *   **MTA** - Supports all Message delivery functionality including Adaptive Delivery. Optionally, also supports Message Generation.

    *   **Platform DB**    - Stores all templates, recipient lists, and generation task data.

    *   **Event Hose**      – Distributes all system events to the Analytics node and Webhook subscriptions.

*   Analytics Role

    *   **Analytics DB**    – Stores aggregated data of all system events delivered by the event hose.

    *   **Web User Interface**                – Provides graphical reporting summaries, template editing and management, recipient list storage management, and authentication key generation and management.

    *   **HTTP Proxy Service**               - Supports all REST API including message generation, administration, and metrics (reporting) functions.

### Note

You do not need to install all roles. Also, some sub-roles can be deployed on separate nodes. Listing all possible permutations is not feasible. Please consult with a Momentum Product Manager for more information on highly distributed deployments.

| [Prev](p.installing.php)  | [Up](p.installing.php) |  [Next](hardware.config_options.php) |
| Part II. Installing Momentum  | [Table of Contents](index.php) |  5.2. Configuration Options |

Follow us on:

[![Facebook](https://support.messagesystems.com/images/icon-facebook.png)](http://www.facebook.com/messagesystems) [![Twitter](https://support.messagesystems.com/images/icon-twitter.png)](http://twitter.com/#!/MessageSystems) [![LinkedIn](https://support.messagesystems.com/images/icon-linkedin.png)](http://www.linkedin.com/company/message-systems)