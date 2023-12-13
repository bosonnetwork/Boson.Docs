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

# Super Nodes

A boson super node, also known as a bootstrap node, is a specific type of DHT node that primarily assists new nodes in joining the boson network. It accomplishes this by propagating nodes into the routing tables of neighboring nodes, and ensuring the health and stability of those routing tables. Since super nodes act as bootstrap nodes, they need to be hosted on a VPS with a public IP address.

In addition to their role as bootstrap nodes, boson super nodes provide essential built-in services, including Web Gateway and Active Proxy services. The network's development will see the integration of more built-in services as it progresses.

{% hint style="info" %}
We anticipate the active participation of the community in deploying public super nodes to enhance the health and robustness of the Boson network. Please keep us informed once you commence work on this initiative."
{% endhint %}

## Public Boson Super Nodes

The Trinity Tech team has deployed and published a list of Boson super nodes for public use. Each of these super nodes is currently operational and offers support for Active Proxy and Web Gateway services. Please check [here](https://github.com/bosonnetwork/public-super-nodes/blob/master/public-super-nodes.json) to get the details.

* [Public boson super nodes](https://github.com/bosonnetwork/public-super-nodes/blob/master/public-super-nodes.json)

### A Config Sample for The Community

When the community opts to establish a Boson super node for public or experimental use, a well-configured file is essential. This configuration file should specify several super nodes to serve as bootstrap nodes for initial connections. Once the super node is operational, it will automatically establish connections to the boson network in a gradual manner through these designated bootstrap nodes

Provided below is an example configuration file for the community's use. We are delighted to witness the growing presence of public super nodes within the community.

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
      "class": "io.bosonnetwork.service.dhtproxy.DHTProxy",
      "configuration": {
        "port": 8088
      }
    },
    {
      "class": "io.bosonnetwork.service.activeproxy.ActiveProxy",
      "configuration": {
        "port": 8090,
        "portMappingRange": "20000-22000",
        "connections":8,
        "maxConnections":64,
        "peerPrivateKey": "YOUR-PRIVATE-KEY-TO-PEER"
      } 
    }
  ]  
}
```

## More Links

* [Boson Super Nodes](super-nodes.md#boson-super-nodes)
* [Setting up a Boson super node by the community](broken-reference)
* [Java SDK API document](../developer-kits/java.md)
