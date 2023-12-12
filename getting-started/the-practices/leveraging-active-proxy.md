# Leveraging Active Proxy

The Active Proxy service serves as a system-level component operating seamlessly across the network. Its core purpose lies in facilitating the forwarding of locally deployed services within a home WiFi environment, ensuring accessibility to the public.

The complete service comprises two integral components: **Service** and **Client**. The service component operates in tandem with the super node, and users typically do not need to be concerned about this aspect. On the other hand, the client part is designed to run alongside the regular photon node. Given that the regular node is often integrated into user applications, it can be easily customized to meet specific requirements or align with different application scenarios.

## Deploying Active Proxy Service

As mentioned above, the Active Proxy service operates in tandem with the super node on a server with a public address. Below is an example of a configuration file that can serve as a reference:

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
  ],
  
  "services": [
    {
      "class": "io.bosonnetwork.service.activeproxy.ActiveProxy",
      "configuration": {
        "port": 8090,
        "portMappingRange": "20000-22000",
        "connections":8,
        "maxConnections":64,
        "peerPrivateKey": "THE-PEER-PRIVATE-KEY-OF-ACTIVE-PROXY-SERVICE",
      } 
    }
  ]
}
```

The Active Proxy service propagates across the Boson network and can be identified as a peer through a peer ID. To retain ownership of this peer service, the deploying user is required to specify the <mark style="color:green;">`peerPrivateKey`</mark> item with a private key value. It is essential to note that only with this private key can the peer information of this service be updated later as needed.

## Launch an Active Proxy Client

Users can build the Active Proxy client in Debian package with the following nomenclature `boson-meerkat.deb` on a Debian-based Linux system by running the commands:

```bash
$ git clone git@github.com/bosonnetwork/Photon photon
$ cd photon/build
$ mkdir prod && cd prod
$ cmake -DCMAKE_INSTALL_PREFIX=dist ../..
$ make -jN
$ make install
$ make meerkat-deb

```

After completing the build, a Debian package with the name `boson-meerkat.deb` is generated. The user can install this package and keep it running as a system service.

```bash
$ sudo dpkg -i boson-meerkat.deb
$ sudo systemctl status boson-meerkat
```

Here is the config file used by the boson-meerkat service running as the active proxy client.

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39002,
  "dataDir": "/var/lib/boson-meerkat",

  "logger": {
    "level": "info",
    "logFile": "/var/log/boson-meerkat/boson.log",
    "pattern": "[%Y-%m-%d %T] [%n] %^[%l] %v%$"
  },

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    }
  ],
  "addons": [
    {
      "name": "ActiveProxy",
      "configuration": {
        "serverPeerId" : "5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6",
        "upstreamHost": "127.0.0.1",
        "upstreamPort": 8989
      }
    }
  ]
}
```

## Deploying a Home-Based Service

To showcase the functionality of the Active Proxy service, deploying a personal website service on your home LAN, along with the Active Proxy client, is necessary. Initially, this website can only be accessed within your LAN environment. However, by leveraging the Active Proxy service, the access point to this website service will be forwarded to a Boson super node, thereby enabling accessibility to the public outside your LAN.\
\
In the aforementioned example, the local web service is assumed to be running on port 8989 and the loopback address. You can verify its functionality by accessing the URL - [http://127.0.0.1:8989](http://127.0.0.1:8989). By employing the Active Proxy client, the website becomes accessible to the public outside your local environment.

## More Links

* [**Generating a private key for service peer**](the-interactive-shell-command.md#a-java-based-shell-command)
* [**Register a pc2 domain name to map the personal service**](../../operations/pc2.net.md#registering-a-pc2-domain-name)
* [**Check the pc2 domain name whether is bound with the correct nodeId**](../../operations/pc2.net.md#checking-pc2-domain-names)
