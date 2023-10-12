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
        "peerPrivateKey": "d7f3d9cbd61a65c06d2f81986403214ba563a18042c1615d84dd01ef53e09e32825ed1d126c05b7d2a65845f9686d39fa72a7b2be8b83b3f181c88c6e44bbac5",
      } 
    }
  ]
}
```

In this config file, only one item of 'ActiveProxy' service is included. Users can use the other port value or port range other than the default values.

The service over the Carrier network is broadcasted and located as a peer information and identified by using peerId. The deploying user needs to maintain ownership of this peer so that the service can be updated and broadcasted later if necessary. Therefore, the item peerPrivateKey is the secret key to control the ownership of this peer and needs to be kept private.

{% hint style="info" %}
The Trinity-Tech team has deployed a list of carrier super nodes that can be leveraged by the user applications. One set of these carrier super nodes provides the Active Proxy service with supporting the pc2 domain name. &#x20;
{% endhint %}

## The Leverage of Active Proxy Client



## Configuration of Active Proxy Service in the Carrier Node Application

An application, named "`Launcher`," is utilized as a daemon service running as a Native DHT node to make use of the Active Proxy service. The appropriate configuration for this is illustrated in the following example:

```json
{
  "ipv4": true,
  "ipv6": false,
  "dataDir": "./data",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    },
	  // more bootstrap nodes
  ],

  "services": [
    {
      "name": "ActiveProxy",
      "configuration": {
        "serverId": "YOUR-TARGET-CARRIER-SUPER-NODE-ID",
        "serverHost": "TARGET-CARRIER-SUPER-IP-ADDRESS-OR-HOSTNAME",
        "serverPort": "TARGET-ACTIVE-PROXY-SERVICE-PORT",
        "upstreamHost": "YOUR-SERIVCE-IP-ADDRESS", // local IP address
        "upstreamPort": "YOUR-SERVICE-PORT"
      }
    }
  ]
}
```

💡 Notice: The "\`Launcher\`" application can be constructed under the "launcher" directory of the \[Elastos.Native]\([https://github.com/elastos/Elastos.Carrier.Native](https://github.com/elastos/Elastos.Carrier.Native)) repository.

Here are the explanations for the fields used in “services” part of the service configuration file:

* **Name:** The name of the target service.
* **configuration.serverId:** The Node ID of the target super carrier node.
* **configuration.serverHost:** The IP address of the carrier super node.
* **configuration.serverPort:** The active port number of the proxy service.
* **configuration.upstreamHost:** The host name or IP address of the local service to be mapped out.
* **configuration.upstreamPort:** The port number of the local service to be mapped out.

## llRun a local service to be forwarded

Deploy a local website service on a Raspberry Pi device in a LAN environment. The website should be accessible at [http://192.168.1.101:80](http://192.168.1.101/)within the local network. Once the website is deployed, launch the `launcher` service using the "sample.conf" configuration file on the same Raspberry Pi device.

```json
{
  "ipv4": true,
  "ipv6": false,
  "dataDir": "./data",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    },
	  // more bootstrap nodes
  ],

  "services": [
    {
      "name": "ActiveProxy",
      "configuration": {
        "serverId": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
        "serverHost": "155.138.245.211",
        "serverPort": 8090,
        "upstreamHost": "192.168.1.101", // local IP address of your raspberry device
        "upstreamPort": 80 // http-based website.
      }
    }
  ]
}
```

with the command under a directory with “**launcher**” binary

```sh
$ ./launcher -c sample.conf
```

Once you have launched the `launcher` service, the Carrier Super Node will assign a mapped port for your service. In my case, the assigned port is `20000`, which is the first port in the mapping range.

To check if your website is working properly, you can access it at [http://155.138.245.211:20000](http://155.138.245.211:20000/).
