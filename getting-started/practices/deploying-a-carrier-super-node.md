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

# Deploying a Carrier Super Node

{% hint style="info" %}
_It is recommended to install the carrier super node on **Ubuntu 22.04** or later, and it must be bound to a public IP address. Otherwise, it cannot function as a bootstrap node._
{% endhint %}

## Installation of Runtime Dependencies

The following runtime components are dependencies that must be installed prior to installing the carrier super node service:

* Java Virtual Machine (JVM) >= Java 11
* sodium (libsodium) >= 1.0.16

To install these dependencies, please run the following commands:

{% code fullWidth="true" %}
```sh
$ sudo apt install openjdk-11-jre-headless libsodium23
```
{% endcode %}

## Building the Super Node Debian Package

After installing the dependencies listed above on your build machine, execute the following commands to build the carrier super node package, which will be referred to as the carrier Debian package:

```sh
$ git clone git@github.com:elastos/Elastos.Carrier.Java.git SuperNode
$ cd SuperNode
$ ./mvnw -Dmaven.test.skip=true
```

After the build process finishes, the Debian package will be generated in the directory `launcher/target` with the name pattern _**carrier-launcher-\<version>-\<timestamp>.deb**_. The values of <_**version**_> and <_**timestamp**_> will vary depending on the specific version being built.

## Installing the Carrier Super Node

Upload the generated Debian package to the target VPS, and then run the following command to install it as a super node service:

```sh
$ sudo dpkg -i carrier-launcher-<version>-<timestamp>.deb
```

The super node installation includes several directories and files with the following organized structure:

* **/usr/lib/carrier**: contains the runtime libraries, including jar packages
* **/etc/carrier**: contains the configuration file default.conf
* **/var/lib/carrier**: contains the runtime data store
* **/var/log/carrier**: contains the output log file carrier.log
* **/var/run/carrier**: contains the runtime directory.

while the data files cached under **`/var/lib/carrier`** has the following structure:

* **key**: contains a randomly generated private key.
* **id**: contains the node ID.
* **dht4.cache**: contains the routing table information for IPv4 addresses.
* **dht6.cache**: contains the routing table information for IPv6 addresses, if IPv6 is enabled.
* **node.db**: contains information about Value and PeerInfo.

## Enable the Opening of the Port

If your VPS is running the super node service and has a firewall enabled, you will need to open the designated port. The default port for usage is **`39001`**. To enable the port or check if it's already enabled, run the following commands with privileged permission:

{% code overflow="wrap" fullWidth="false" %}
```sh
$ sudo ufw allow 39001/udp
$ sudo ufw status verbose
```
{% endcode %}

## Checking Super Node Status

Once the carrier super node has been installed and started running on your VPS, it's recommended to use the 'systemctl' command to check the status of the service or to start/stop the service.&#x20;

```bash
$ systemctl status carrier
$ sudo systemctl start carrier
$ sudo systemctl stop carrier
```

Additionally, review the log file for more detailed information on the current running status.

```sh
$ tail -f /var/log/carrier/carrier.log
```

## An Example File for Configure

To properly run the carrier super node service, update the config file with the following contents, but make sure to fill in your own address4 or address6 field.&#x20;

```json
{
  "ipv4": true,
  "ipv6": false,
  "address4": "your-ipv4-address",
  "address6": "your-ipv6-address",
  "port": 39001,
  "dataDir": "/var/lib/carrier",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    },
    {
      "id": "FRkR2NWhbSGMv3BqGui7FYAgCSAWySrz6xmTAx9Ny7zo",
      "address": "45.76.161.175",
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
    },
    {
      "id": "5BJ8SZZQ4z4izhw82W2ksyuTCQz3GwWUWBSaza4qzVT9",
      "address": "207.148.82.19",
      "port": 39001
    }
  ] 
}
```
