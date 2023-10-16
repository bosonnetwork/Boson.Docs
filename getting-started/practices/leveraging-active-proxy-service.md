# Leveraging Active Proxy Service

Active Proxy service is a system-level service that operates over the carrier network. Its purpose is to forward locally deployed personal service within a LAN network, making them accessible to the public.

Active Proxy service consists of two parts: the **Service** and **Client**. The service part runs alongside the super node, and users typically do not need to be concerned about this aspect. The client part runs alongside the native node of the Carrier. As the native Carrier is often integrated into the user application, it can be customized based on specific requirements or application scenarios.

## Deploying the Active Proxy Service

As mentioned, the Active Proxy service is running alongside the super node on the server with a public address. Here is an example of a config file that can be referenced.

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
    } // more bootstrap nodes. 
  ],
  
  "services": [
    {
      "class": "elastos.carrier.service.activeproxy.ActiveProxy",
      "configuration": {
        "port": 8090,
        "portMappingRange": "20000-22000",
        "peerPrivateKey": "THE-PEER-PRIVATE-KEY-OF-ACTIVE-PROXY-SERVICE",
      } 
    }
  ]
}
```

In the config file above, only one item of the **ActiveProxy** service is included in the **services** section. Users can update the port value or port range values as required.

The Active Proxy service is propagated over the carrier network, and it can be located or identified as a peer by using a peer ID. To maintain ownership of this peer service, the deploying user needs to specify the **peerPrivateKey** item with a private key value. Only with this private key the peer information of this service can be updated later as required.

{% hint style="info" %}
The Trinity-Tech team has deployed a list of carrier super nodes hosting Active Proxy service that can be leveraged by the user applications. One set of these carrier super nodes provides the Active Proxy service with supporting the pc2 domain name. &#x20;
{% endhint %}

## To Launch an Active Proxy Client

In the client part, the Active Proxy client can be integrated into the application and run in either of these two ways:

* Run as a general command application, or
* Run as a system service named **carrier-meerkat** on Debian-based Linux.

### 1. Run the Active Proxy Client as a General Command Application&#x20;

Users can build the Active Proxy Client application on Unix-based Linux or Windows, and run it as an application by executing the following commands:

```bash
$ git clone git@github.com:elastos/Elastos.Carrier.Native carrier2
$ cd carrier2/build
$ mkdir prod && cd prod
$ cmake -DCMAKE_INSTALL_PREFIX=dist ../..
$ make -jN
$ make install
```

After successfully completing the build, launch the Active Proxy client using the following command:

```sh
$ ./dist/bin/carrier-launcher -c YOUR-PATH/default.conf
```

Here is an example of a config file for your reference.

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39002,
  "dataDir": "YOUR-DATA-PATH",

  "logger": {
    "level": "info",
    "logFile": "YOUR-DATA-PATH/carrier.log",
    "pattern": "[%Y-%m-%d %T] [%n] %^[%l] %v%$"
  },

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    } // more super nodes can be added next.
  ],
  "addons": [
    {
      "name": "ActiveProxy",
      "configuration": {
        "serverPeerId" : "5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6",
        "peerPrivateKey": "THE-PEER-PRIVATE-KEY-OF-YOUR-LOCAL-SERVICE",
        "domainName": "abc.pc2.net",
        "upstreamHost": "127.0.0.1",
        "upstreamPort": 8989
      }
    }
  ]
}
```

In the config file above, the `serverPeerId` item represents the peer ID in base58 format for the Active Proxy service that you want to use. The four subsequent items should be configured based on your personal micro-service deployed on your home LAN. Here the item `peerPrivateKey` is the private key used to control the ownership of your personal service as for the Active Proxy service on super node. The others are the parameters related to the personal service that you can update them according the environment.

### 2. Run the Active Proxy Client as a System Service

Users can also build the Active Proxy client in Debian package with name `carrier-meerkat.deb` on a Debian-based Linux system by using the following commands:

```bash
$ git clone git@github.com/elastos/Elastos.Carrier.Native carrier2
$ cd carrier2/build
$ mkdir prod && cd prod
$ cmake -DCMAKE_INSTALL_PREFIX=dist ../..
$ make -jN
$ make install
$ make meerkat-deb

```

After completing the build, a Debian package named `carrier-meerkat.deb` is generated. The user can install this package and keep it running as a system service.

```bash
$ sudo dpkg -i carrier-meerkat.deb
$ sudo systemctl status carrier-meerkat
```

In this case, it is recommended to run the Active Proxy client with the following config example:

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39002,
  "dataDir": "/var/lib/carrier-meerkat",

  "logger": {
    "level": "info",
    "logFile": "/var/log/carrier-meerkat/carrier.log",
    "pattern": "[%Y-%m-%d %T] [%n] %^[%l] %v%$"
  },

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    } // more super nodes can be added next.
  ],
  "addons": [
    {
      "name": "ActiveProxy",
      "configuration": {
        "serverPeerId" : "5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6",
        "peerPrivateKey": "THE-PEER-PRIVATE-KEY-OF-YOUR-LOCAL-SERVICE",
        "domainName": "abc.pc2.net",
        "upstreamHost": "127.0.0.1",
        "upstreamPort": 8989
      }
    }
  ]
}
```

## Deploying a Personal Web Service at Your Home LAN

To demonstrate the use of the Active Proxy service, you need to deploy a personal website service on your home LAN along with the Active Proxy client. Initially, this website can only be accessed within your LAN environment. However, by utilizing the Active Proxy service, the access point to this website service will be forwarded to a carrier super node, allowing it to be accessible to the public outside.

Users can either use **nginx** or other HTTP proxy tools to deploy such a personal website or even use an existing local service. Here is a quick way to run a simple website to demonstrate the power of the Active Proxy service with the following two items:

* proxy tool - caddy ([https://caddyserver.com/download](https://caddyserver.com/download))
* website content ([https://github.com/ColorlibHQ/AdminLTE](https://github.com/ColorlibHQ/AdminLTE))

Download the source website content, and run the **caddy** tool under the directory with a command:

```bash
$ caddy file-server --listen=0.0.0.0:8989
```

Suppose that the device for running this personal website on your local LAN is **192.168.1.100**, then you can check the website in a browser using the URL - [**http://192.168.1.100:8989**](http://192.168.1.100:8989)\
With the Active Proxy client, the website can be accessed by the public outside.

## More Links

* [**Generating a private key for service peer**](the-interactive-shell-command.md#a-java-based-shell-command)
* [**Register a pc2 domain name to map the personal service**](../../operations/pc2.net.md#registering-a-pc2-domain-name)
* [**Check the pc2 domain name whether is bound with the correct carrier nodeId**](../../operations/pc2.net.md#checking-pc2-domain-names)
