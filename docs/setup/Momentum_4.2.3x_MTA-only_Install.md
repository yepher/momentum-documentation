# Momentum 4.2.31 MTA-only Install

This is an example of what install instruction might looking in MarkDown.

_Ported from [Momentum_4.2.31.1_MTA-only_installation.pdf](https://support.messagesystems.com/package.php/Momentum_4.2.31.1_MTA-only_installation.pdf)_

## CONTENTS

* Introduction
* Download the Software Bundle
* Installing MTA-only cluster configuration
	* Disable Postfix and QPIDD
	* Install the Packages
		* Cluster Manager Node
		* MTA Nodes
* Configuring the Nodes
	* Configure the Cluster Manager
	* Configure Remaining MTA Nodes
* Start Services on the MTA nodes


## Introduction

Before following this procedure you should follow [Momentum Setup CentOS7 Prep](Momentum_Setup_CentOS7_Prep.md) first.

A full-featured version installation of Momentum 4.x has several components that are ancillary to the core MTA functionality. The Cassandra and Vertica databases require separate drive partitions and significantly impact performance if the supporting hardware is not appropriately sized to support
them.

The MTA-only configuration will operate on the Momentum 3.6 hardware footprint, and is intended primarily for the upgrade of existing customers currently running Momentum 3.x, and for new Momentum on-premise installations in a Redhat Enterprise 6 or 7 operating environment that do not need those components of the latest full-featured 4.2.1.x maintenance release that are ancillary to the core MTA functionality. Thus, the 4.2.31 MTA-only installation has the following characteristics:

* no 4.x REST APIs and message generation (SMTP only)
* no Cassandra database
* no Analytics node/functionality, thus no Vertica database and no web UI.
* no Webhooks support

Following initial installation of the Momentum `4.2.31` MTA-only release configuration, the 4.x Webhooks function and/or the REST Transmission API and Inline Message Generation functions can be added in separate procedures if desired. In `4.2.31`, these features no longer require the installation of the Cassandra database. Instructions for adding these capabilities are available from Momentum Customer Support. Please contact them before doing the upgrade if the additional functionality is desired.


## Download the Software Bundle

1. Download the appropriate Momentum software bundle from the Message Systems Support website for every node that you will install or upgrade.

2. Copy the bundle to the `/var/tmp/` directory on each of the nodes. 


**Note**: that throughout this document, specific bundle filenames shown, and their resulting install directory names, are only examples.

```bash
cp momentum-mta-bundle-4.2.31.59853.rhel7.x86_64.tar.gz /var/tmp/
```

* **Note:** if you are using Centos6, then specify rhel6 in the bundle filename instead of rhel7. 
* **Note:** The 4.2.31 MTA-only bundle contains all the necessary components for a subsequent enabling of the 4.x Webhooks and/or the REST APIs and Message Generation after the initial installation.

3. Unpack the tarball on each node, and set the repository directory.

```bash
cd /var/tmp
tar -zxf momentum-mta-bundle-4.2.31.59853.rhel7.x86_64.tar.gz
cd momentum-mta-4.2.31.59853/
./setrepodir
```

* **NOTE:** The `./setrepodir` script establishes some environmental parameters for the installation. If the installation is not completed within this same terminal session as it was started in, the `./setrepodir` command must be re-executed in any new session(s) prior to executing any of the yum commands for the installation.

4. Confirm your valid Momentum license file is in the `/opt/msys/ecelerity/etc` folder on each MTA node. Your licenses should be pulled automatically once they have been issued.

5. If your node does not have public internet access during installation, you will need to add your valid Momentum license files manually.

## Installing MTA-only cluster configuration

**Disable Postfix and QPIDD**

Disable the _Postfix_ software on all the nodes, which would interfere with Ecelerity's SMTP functionality. Disable _qpidd_, which can interfere with RabbitMQ. You can ignore any errors that may appear. These commands can be executed safely without first knowing if _Postfix_ or _qpidd_ are present on the node.

```
service postfix stop
/sbin/chkconfig postfix off
service qpidd stop
/sbin/chkconfig qpidd off
```

### Install the Packages

#### Cluster Manager Node

Identify which server will be the Cluster Manager. This will be the first node we will be installing. This node will serve as the configuration server and host the Postgres database.

This node can also serve as a Log Aggregator if log aggregation is needed. If log aggregation is not desired, then the Cluster Manager will also serve as an MTA node.

* Install these packages on the Cluster Manager node, if log aggregation is desired.

```
cd /var/tmp/momentum-mta-4.2.31.59853

yum install -y --config momentum.repo --enablerepo momentum \
	 msys-role-manager \
	 msys-role-db \
	 msys-ecelerity-mobility-db
```

* Install these packages on the Cluster Manager node, if log aggregation is not desired. In this case, this node will also serve as an MTA, and additional packages for that role will be installed in subsequent steps.

```
cd /var/tmp/momentum-mta-4.2.31.59853

yum install -y --config momentum.repo --enablerepo momentum \
	 msys-ecelerity-config-server \
	 msys-role-db \
	 msys-ecelerity-mobility-db
```


#### MTA Nodes

For every node you designate as an MTA (including the Cluster Manager if not using log aggregation), perform the following:

```
cd /var/tmp/momentum-mta-4.2.31.59853

yum install -y --config momentum.repo --enablerepo momentum \
	 msys-role-mta \
	 msys-role-mobility \
	 msys-ecelerity-engagement-proxy
```

### Configuring the Nodes

#### Configure the Cluster Manager

The Cluster Manager requires the installation and configuration of some additional services. It is also a convenient place to set up stub files that will make the rest of the configuration go much faster.

1. Ensure you have a valid Momentum license file installed on each MTA in the `/opt/msys/ecelerity/etc` directory. A Log Aggregator node does not require a license. If your license has been issued and your server has external connectivity, you can run the following command to pull your license:

`/opt/msys/ecelerity/bin/ec_lic -f`

For more information, see Section 6.1, “Momentum License" on the Message Systems Support website

2. Create a random service password file named `.svcpasswd` that can be used by the various services to access the database. Create the file on the Cluster Manager, then copy it to all Platform nodes _(in the same created location)_.

Additionally, logging into the console remotely or making manual changes and committing them to the shared configuration repository requires an additional username/password combination. By convention, this user is "admin" but you can use any username you want.

```
mkdir -p /opt/msys/etc
< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c8 \
	> /opt/msys/etc/.svcpasswd
	
# before the next command, repeat the creation (mkdir command) of
# the /opt/msys/etc directory on each of the other MTAs
scp -r /opt/msys/etc/.svcpasswd \
	 mtaN.yourdomain.com:/opt/msys/etc/
 
export SVCPASSWD=`cat /opt/msys/etc/.svcpasswd`
export ADMINPASS=admi
```

3. Create the PostgreSQL database host file. Ecelerity requires a PostgreSQL database for console authentication and other minor modules. This is a very low usage database that is installed on the Cluster Manager for simplicity.

```
MyHostName=`hostname -f`
echo $MyHostName > /opt/msys/etc/.dbhost
```

4. Configure PostgreSQL with the Ecelerity schema.

```
service msyspg start
sleep 40
cd /opt/msys/ecelerity/etc
../bin/init_schema --password $SVCPASSWD \
					  --admin-password $ADMINPASS
```

You should see something like this:

```
Loading sql/common.sql into common...done!
Loading sql/console.sql into console...done!
Loading sql/returnpath.sql into returnpath...done!
Loading sql/seedlist.sql into seedlist...done!
Loading sql/adaptive.sql into adaptive...done!
```

5. Only if there were any problems creating the Ecelerity database in PostgreSQL, invoke the following command:

**NOTE:** **DO NOT** run this command if this there were no errors when executing init_schema in the previous step

```
/opt/msys/3rdParty/bin/dropdb -U ecuser ecelerity

# Then try to run init_schema again
```

## Configure Ecelerity on the Cluster Manager using ecconfigd

### Configure and start ecconfigd

1. Edit `/opt/msys/ecelerity/etc/ecconfigd.conf`

* Replace

```bash
UseCanonicalName DNS
```

* with

```bash
ServerName mta1.yourdomain.com
```

* and comment out the following line with the `#` symbol:

```bash
Include "/opt/msys/etc/installer/ecconfigd.d/*.conf"
```
 
2. Display the service password and copy it to your clipboard so that is it easily accessible for upcoming commands.

```bash
echo $SVCPASSWD
```

3. Format the password for Subversion. Enter or paste the service password when prompted.

**NOTE:** only the _first_ htdigest command should have the -c option: including that in subsequent htdigest commands will cause later problems.

```bash
echo $SVCPASSWD
/opt/msys/ecelerity/bin/create_ssl_cert ecconfigd $MyHostName \
		 /var/ecconfigd/apache
		 
# htdigest prompts for the password twice and does not support
# shell redirection. make sure you copied the service password
# into your clipboard, i.e. the contents of $SVCPASSWD,
# which we just copied in the previous step
/opt/msys/3rdParty/apache/sbin/htdigest -c \
 		/var/ecconfigd/repo/svn-auth.htdigest "ecconfigd repo" ecuser 
 		
```


4. Configure the admin user. Enter or paste the admin password when prompted.

```bash
# Use your admin password here (typically "admin",
# i.e. the contents of $ADMINPASS)
echo $ADMINPASS
/opt/msys/3rdParty/apache/sbin/htdigest \
		 /var/ecconfigd/repo/svn-auth.htdigest \
		 "ecconfigd repo" admin
```

5. Start up the ecconfigd service to complete the ecconfigd setup.

```bash
service ecconfigd start
```

### Bootstrap the initial Ecelerity configuration repository.

1. Set the proper permissions on the directory

```bash
cd /opt/msys/ecelerity/etc
chmod g+ws .
```

2. If you are installing a cluster of multiple MTA nodes, with or without a log aggregator, then invoke

```bash
sudo -u ecuser /opt/msys/ecelerity/bin/eccfg bootstrap \
		 --clustername default \
		 --username admin --password $ADMINPASS
```

Otherwise, if you are installing a singlenode instance, then invoke

```bash
sudo -u ecuser /opt/msys/ecelerity/bin/eccfg bootstrap \
		 --singlenode \
		 --username admin --password $ADMINPASS	 
```

Your results should look like this:

```bash
A /opt/msys/ecelerity/etc/conf/default
A /opt/msys/ecelerity/etc/conf/default/ecelerity.conf
A /opt/msys/ecelerity/etc/conf/default/mobile.conf
A /opt/msys/ecelerity/etc/conf/default/common.conf
A /opt/msys/ecelerity/etc/conf/default/eccluster.conf
A /opt/msys/ecelerity/etc/conf/default/messagescope.conf
A /opt/msys/ecelerity/etc/conf/default/messagescope_remediation.conf
A /opt/msys/ecelerity/etc/conf/default/ecelerity-cluster.conf
```

**Note:** If there is an error during this step, you can move the entire
`/opt/msys/ecelerity/etc/conf` directory to a different location, such as `/tmp`, try to correct the errors received, and then try to bootstrap a second time.

3. If installing multiple nodes, setup the cluster configuration. **Skip this step for single node installs**.

Copy the `msgc_server.con` file to the appropriate location.

```bash
cp /opt/msys/ecelerity/etc/sample-configs/default/msgc_server.conf \
 /opt/msys/ecelerity/etc/conf/global/
```

Edit the following lines in `/opt/msys/ecelerity/etc/conf/global/msgc_server.conf`. For EACH MTA node that you are installing, substitute the hostnames and IP addresses as appropriate.

**Skip this step for single node installs**.

```bash
msgc_server {
	 peers = [
		 mta1.yourdomain.com = "10.77.0.219"
		 mta2.yourdomain.com = "10.77.1.6"
		 ...
		 mtaN.yourdomain.com = "10.77.1.10"
	 ]
}
```

4. Create an `/opt/msys/ecelerity/etc/conf/default/ecdb.conf` with the database source information.

```bash
cat << EOT > /opt/msys/ecelerity/etc/conf/default/ecdb.conf
Datasource "ecdb" { uri = (
"pgsql:host=$MyHostName;dbname=ecelerity;user=ecuser;password=$SVCPASSWD" )}
EOT
```

5. Update the `eccluster.conf` file.

Replace the following line in the `/opt/msys/ecelerity/etc/conf/default/eccluster.conf` file:

```bash
readonly_include "/opt/msys/etc/installer/eccmgr.d/ecdb.conf"
```

with this line:

```bash
readonly_include "ecdb.conf"
```

6. Make this update to the `ecelerity-cluster.conf` configuration file, but **ONLY IF** you are performing a multiple node install **AND ONLY IF** the first node is a Log Aggregator. Remove the aggregator comment prefix _(#aggr#)_ wherever it occurs within `/opt/msys/ecelerity/etc/conf/default/ecelerity-cluster.conf`. (The lines shown here are not the totality of the file.)

```bash
#aggr# ec_logger "ec_logger_cluster" {
#aggr# mainlog = "cluster:///var/log/ecelerity/mainlog.cluster=>master"
#aggr# paniclog = "cluster:///var/log/ecelerity/paniclog.cluster=>master"
#aggr# rejectlog = "cluster:///var/log/ecelerity/rejectlog.cluster=>master"
#aggr# acctlog = "cluster:///var/log/ecelerity/acctlog.cluster=>master"
#aggr# }
#aggr# bounce_logger "bounce_logger_cluster" {
#aggr# bouncelog = "cluster:///var/log/ecelerity/bouncelog.cluster=>master"
#aggr# }
cluster {
 logs = [logs = [
#aggr# rejectlog = "/var/log/ecelerity/rejectlog.cluster"
#aggr# paniclog = "/var/log/ecelerity/paniclog.cluster"
#aggr# mainlog = "/var/log/ecelerity/mainlog.cluster"
#aggr# acctlog = "/var/log/ecelerity/acctlog.cluster"
#aggr# bouncelog = "/var/log/ecelerity/bouncelog.cluster"
 ]
}
```

7. Update the /opt/msys/ecelerity/etc/conf/default/ecelerity.conf configuration file.

* Replace this line:

```bash
readonly_include "/opt/msys/etc/installer/ecelerity.d/"
```

With this line:

```bash
 readonly_include "ecdb.conf"
```

If you are performing a multiple node install, include the cluster configuration file by removing the comment character `#` from the line

```bash
# include "ecelerity-cluster.conf"
```

_(Bootstrap the initial Ecelerity configuration repository,Step 7: continued)_

Disable `event_hydrant` and `event_hose` in the `/opt/msys/ecelerity/etc/conf/default/ecelerity.conf` configuration file. Add the comment character `#` to the following 4 lines

```bash
# Add the comment character (#) to the following 4 lines
event_hydrant "event_collector" {
}
event_hose "momentum_metrics" {
}
```

Commit the changes.

```bash
sudo -u ecuser /opt/msys/ecelerity/bin/eccfg commit \
	 --username admin --password $ADMINPASS \
	 --add-all --message "Including cluster config config"
```

8. Test the Ecelerity configuration. Enter the username `'admin'` and your `$ADMINPASS` password when prompted.

```bash
/opt/msys/ecelerity/bin/ec_console shim://
# Login with admin/$ADMINPASS.
# After logging-in you will get a ">" prompt, and be able to type
# various commands, such as "version" and "summary"
quit
```

9. Depending on the first node's role, Log Aggregator or MTA, start the relevant service

```bash
# If the first node is a Log Aggregator
/etc/init.d/eccmgr start

# If the first node is an MTA
/etc/init.d/ecelerity start
```

### Configure Remaining MTA Nodes

1. To ease configuration of remaining MTA nodes, copy the entire contents of the configuration directory FROM the first node (the Cluster Manager, which is either a Log aggregator or MTA),
TO ALL the remaining MTA nodes.

For each remaining MTA node in the cluster,

```bash
scp -r /opt/msys/ecelerity/etc \
		 mtaN.yourdomain.com:/opt/msys/ecelerity
```

**NOTE:** Because the above command overwrites the license files on the target nodes, you must remove the files and then re-pull them using the below command

```bash
/opt/msys/ecelerity/bin/ec_lic -f
```

2. Log onto each remaining MTA node in the cluster and bootstrap the Ecelerity configuration repo.

```bash
cd /opt/msys/ecelerity/etc/
chown -R ecuser:ecuser /opt/msys/ecelerity/etc/
chmod g+ws .
chmod -R g+w .

sudo -u ecuser /opt/msys/ecelerity/bin/eccfg bootstrap \
		 --clustername default \
		 -u admin -p $ADMINPASS FIRST.NODE.FQDN
```

3. For each MTA node, test Ecelerity configuration exactly as you did on the first MTA node


```
/opt/msys/ecelerity/bin/ec_console shim://

# Hit enter to get a Username: prompt, and use admin/$ADMINPASS.
# After logging-in you will get a ">" prompt, and be able to type
# various commands, such as "version" and "summary"
quit

```

4. Be sure to repeat the steps in this section on all remaining platform nodes.

**Start Services on the MTA nodes**

```
service ecelerity start
service msys-riak start
```

