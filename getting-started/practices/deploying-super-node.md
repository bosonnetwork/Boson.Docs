---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Deploying Super Node

{% hint style="info" %}
_It is recommended to install a carrier super node on **Ubuntu 22.04** or later, and it must be bound to a public IP address. Otherwise, it cannot function as a bootstrap node._
{% endhint %}

## Installation of Runtime Dependencies

The following runtime components are dependencies that must be installed prior to installing the carrier super node service:

* Java Virtual Machine (JVM) >= Java 11
* sodium (libsodium) >= 1.0.16

To install these dependencies, please run the following command:

{% code fullWidth="true" %}
```sh
$ sudo apt install openjdk-11-jre-headless libsodium23
```
{% endcode %}

## Building the Super Node Debian Package

After installing the dependencies on your build machine, run the following commands to build the super node service as Debian package:

```sh
$ git clone git@github.com:elastos/Elastos.Carrier.Java.git SuperNode
$ cd SuperNode
$ ./mvnw -Dmaven.test.skip=true
$ cd launcher/target
```

After the build, a Debian package will be generated with the pattern name _**carrier-launcher-\<version>-\<timestamp>\_all.deb**_. The values of <_**version**_> and <_**timestamp**_> will  depend on the version number and time of the build.

## Installing the Carrier Super Node Service

Once the Debian package is generated, then run the following command to install it as a super node service:

```sh
$ sudo dpkg -i carrier-launcher-<version>-<timestamp>.deb
```

After the installation, several directories and files with the following organized structure are created if it's a fresh installation:

* **/usr/lib/carrier**:  contains the runtime libraries, including jar packages
* **/var/lib/carrier**:  contains the runtime libraries, including jar packages
* **/etc/carrier**:  contains the config file **default.conf**
* **/var/lib/carrier**:  contains the runtime data store
* **/var/log/carrier**:   contains the output log file carrier.log

A list of runtime data stored and cached under **`/var/lib/carrier`** includes the following files:

* **key**:  contains a randomly generated private key
* **id**:  contains the node ID in base58 format
* **dht4.cache**:  contains the routing table information for IPv4 addresses.
* **dht6.cache**:  contains the routing table information for IPv6 addresses, if IPv6 is enabled.
* **node.db**:  contains information about Value and Peer announced over network.

## Enable Allowing the Opening of Ports

IIf the VPS running the super node service has a firewall enabled, it needs to enable the designated ports. The default port being used is **`39001`**. To enable or check the port if it's already enabled, run the commands with '**`ufw'`** tool below with privileged permission:

{% code overflow="wrap" fullWidth="false" %}
```sh
$ sudo ufw allow 39001/udp
$ sudo ufw status verbose
```
{% endcode %}

## Checking the Super Node Service Status

Once the super node service has been installed and is running on the VPS, it is recommended to use the '**`systemctl`**' command to check the status of the service or to start/stop it for management purposes.

```bash
$ systemctl status carrier
$ sudo systemctl start carrier
$ sudo systemctl stop carrier
```

Below is the command to check the output log for more detailed information on the current running status.

```sh
$ tail -f /var/log/carrier/carrier.log
```

## An Example of a Config File

To properly run the carrier super node service, update the config file with the following contents, but make sure to fill in your own address4 or address6 field.&#x20;

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39001,
  "dataDir": "/var/lib/carrier",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    },
    {
      "id": "6o6LkHgLyD5sYyW9iN5LNRYnUoX29jiYauQ5cDjhCpWQ",
      "address": "45.32.138.246",
      "port": 39001
    },
    {
      "id": "8grFdb2f6LLJajHwARvXC95y73WXEanNS1rbBAZYbC5L",
      "address": "140.82.57.197",
      "port": 39001
    },
    {
      "id": "4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41",
      "address": "107.191.62.45",
      "port": 39001
    }
  ],
  "services": [
    {
      "class": "elastos.carrier.service.dhtproxy.DHTProxy",
      "configuration": {
        "port": 8088
      }
    },
    {
      "class": "elastos.carrier.service.activeproxy.ActiveProxy",
      "configuration": {
        "host": "YOUR-IP-ADDRESS",
        "port": 8090,
        "portMappingRange": "20000-22000",
        "peerPrivateKey": "YOUR-PRIVATE-KEY-OF-ACTIVE-PROXY-PEER"
      }
    }
  ]
}
```

{% hint style="info" %}
The later section of "**services**" is used for the super node to provide the **Active Proxy** service and **DHT Proxy** service. Users can disable those carrier services by removing this section..&#x20;
{% endhint %}
