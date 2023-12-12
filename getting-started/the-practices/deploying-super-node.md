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
_It's recommended to install a boson super node on **Ubuntu 22.04** or a later version. Additionally, the super node must be bound to a public IP address in order to function as a public bootstrap node._
{% endhint %}

To initiate the installation of the essential runtime components required by boson super nodes, please execute the following command on your build machine:

{% code fullWidth="true" %}
```sh
$ sudo apt install openjdk-11-jre-headless libsodium23
```
{% endcode %}

## Building Debian Package

After installing the dependencies on your build machine, execute the following commands to build a Debian package that can be installed as a super boson node:

```sh
$ git clone git@github.com:bosonnetwork/Boson.Distribution.git boson
$ cd boson
$ ./mvnw install
$ cd target
```

After the build, a Debian package is generated with the following **nomenclature** <mark style="color:green;">**boson-\<version>-SNAPSHOT-all.deb**</mark>**.**

## Installing Super Node

After generating the Debian package, proceed to upload it to the VPS server. Then, execute the following command to install it as a super boson node in the server with privileged permission:

```sh
$ sudo dpkg -i boson-<version>--SNAPSHOT-all.deb
```

After the installation, several directories and files with the following organized structure are created if it's a fresh installation:

* **/usr/lib/boson**: contains the runtime libraries, including jar packages
* **/var/lib/boson**: contains the runtime libraries, including jar packages
* **/etc/boson**: contains the config file **default.conf**
* **/var/lib/boson**: contains the runtime data store
* **/var/log/boson**: contains the output log file boson.log

A list of runtime data stored and cached under **`/var/lib/boson`** includes the following files:

* **key**: contains a generated private key
* **id**: contains the node ID in base58 format
* **dht4.cache**: contains the routing table information for IPv4 addresses.
* **dht6.cache**: contains the routing table information for IPv6 addresses, if IPv6 is enabled.
* **node.db**: contains information about Value and Peer announced over network.

## Enable Port Opening

If the VPS running the super node has a firewall enabled, it needs to enable the designated ports. The default port being used is **`39001`**. To enable or check the port if it's already enabled, run the commands with '**`ufw'`** tool below with privileged permission:

{% code overflow="wrap" fullWidth="false" %}
```sh
$ sudo ufw allow 39001/udp
$ sudo ufw status verbose
```
{% endcode %}

## Checking Service Status

Once the super node has been installed and is running on the VPS, it is advisable to employ the 'systemctl' command to check the service status or initiating start/stop actions for effective management.

```bash
$ systemctl status boson
$ sudo systemctl start boson
$ sudo systemctl stop boson
```

Below is the command to check the output log for more detailed information on the current running status.

```sh
$ tail -f /var/log/boson/boson.log
```

## An Example of a Config File

To properly run the boson super node service, update the config file with the following contents, but make sure to fill in your own address4 or address6 field.

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39001,
  "dataDir": "/var/lib/boson",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    }
  ]
}
```
