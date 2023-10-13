# Leverage the ActiveProxy Service

Active Proxy service is a type of system level service over the carrier network. It is used to forward local services that are deployed and running within a LAN network, making them accessible to the public.

The Active Proxy service consists of two parts: the **Service** and **Client**. The service part runs alongside the super node, and users typically do not need to be concerned about this aspect. The other part runs alongside the native node of the Carrier. As the native Carrier is often integrated into the user application, it can be customized and updated based on specific requirements or application scenarios.

## Deploying the Active Proxy Service

As it's mentioned, the Active Proxy service is running alongside the super node on the server with public address. Here is the an example of a config file that can be referenced.&#x20;

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

In this config file, only one item of 'ActiveProxy' service is included. Users can use the other port value or port range other than the default values.

The service over the Carrier network is broadcasted and located as a peer information and identified by using peerId. The deploying user needs to maintain ownership of this peer so that the service can be updated and broadcasted later if necessary. Therefore, the item peerPrivateKey is the private key to control the ownership of this peer and needs to be kept private.

{% hint style="info" %}
The Trinity-Tech team has deployed a list of carrier super nodes that can be leveraged by the user applications. One set of these carrier super nodes provides the Active Proxy service with supporting the pc2 domain name. &#x20;
{% endhint %}

## To Launch an Active Proxy Client

In the client part, the Active Proxy client would be integrated into the application and run in either of these two ways:

* as a general command application, or
* as a system service named "carrier-meerkat" on Debian-based Linux.

### 1. Run the Active Proxy Client as a General Command Application&#x20;

Users can build the Active Proxy Client application on Unix-based Linux or Windows and run it in the foreground by executing the following commands:

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

In the config file above, the `serverPeerId` item represents the peer ID in base58 format for the Active Proxy service that you will be using. The four subsequent items should be configured based on your personal micro-service deployed on your home LAN. It's worth mentioning that the `peerPrivateKey` item is the private key used to control the ownership of your personal service.

###

### 2. Run the Active Proxy Client as a System Service

Users can also build the Active Proxy client in Debian package with name`carrier-meerkat.deb`on a Debian-based Linux system by using the following commands:

```bash
$ git clone git@github.com/elastos/Elastos.Carrier.Native carrier2
$ cd carrier2/build
$ mkdir prod && cd prod
$ cmake -DCMAKE_INSTALL_PREFIX=dist ../..
$ make -jN
$ make install
$ make meerkat-deb

```

After completing the build, a Debian package named `carrier-meerkat.deb` is generated. The user can then install this package as a system service and keep it running in the background.

```bash
$ sudo dpkg -i carrier-meerkat.deb
$ sudo systemctl status carrier-meerkat
```

In this case, it is recommended to run the Active Proxy client with the correct file file, as shown in the following example:

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

As an example of using the Active Proxy service, a personal website service needs to be deployed on your home LAN alongside the Active Proxy client. Originally, the website should only be accessible within your LAN environment. With the leverage of the Active Proxy service, the access point to the personal website service would be forwarded to one carrier super node, making it accessible to the public outside.

Users can either use nginx or other HTTP proxy tools to deploy such a personal website, or even can use a existing local service. Here is a quick way to run a simple personal website to demonstrate the strength of the Active Proxy service.

* proxy tool - caddy ([https://caddyserver.com/download](https://caddyserver.com/download))
* website content ([https://github.com/ColorlibHQ/AdminLTE](https://github.com/ColorlibHQ/AdminLTE))

Download the source website content, and run the caddy under the directory with a command:

```bash
$ caddy file-server --listen=0.0.0.0:8989
```

Suppose that the device for running this personal website on your local LAN is **192.168.1.100**, then you can check the website in a browser using the URL - [**http://192.168.1.100:8989**](http://192.168.1.100:8989)

Once the personal service is running, then update the item values in the config file
