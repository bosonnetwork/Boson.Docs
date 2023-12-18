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

A boson super node, also known as a bootstrap node, is a specific type of node that primarily assists new nodes in joining the boson network. It accomplishes this by propagating nodes into the routing tables of neighboring nodes, and ensuring the health and stability of those routing tables. Since super nodes act as bootstrap nodes, they need to be hosted on servers with a public IP address.

In addition to their role as bootstrap nodes, boson super nodes provide essential built-in services, including Web Gateway and Active Proxy services. The network's development will see the integration of more built-in services as it progresses.

## Public Super Nodes

The **Trinity Tech** team has deployed and published a list of boson super nodes for public use. Each of these nodes is currently operational and offers support for Active Proxy and Web Gateway services. Here is the repository that lists the deployed super nodes:

* [Public boson super nodes](https://github.com/bosonnetwork/public-super-nodes/blob/master/public-super-nodes.json)

Active community participation is crucial for deploying public super nodes to strengthen the health and robustness of the network. Please keep us informed once you commence work on this initiative by pushing pull-request to the above repository. We are delighted to witness the growing presence of public super nodes within the community.

## A Sample for the Community

When the community opts to establish a boson super node for the public or experimental use, a well-configured file is essential. This config file should specify several super nodes to serve as bootstrap nodes for initial connections. Once the super node is operational, it will automatically establish connections to the boson network in a gradual manner through these designated bootstrap nodes

Below is an example configuration file intended for the community's use in deploying a super node through a Debian package.

```json
{
  "ipv4": true,
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
        "peerPrivateKey": "YOUR-PRIVATE-KEY-TO-PEER"
      } 
    }
  ]  
}
```

This config file serves as a simple example, demonstrating the inclusion of a single super  node and an accompanying Active Proxy service. Users have to generate the `peerPrivateKey` for their own peer ID to identify the Active Proxy service provided by this super node.

## More Links

* [**Boson Super Nodes**](../getting-started/boson-protocol/nodes.md#super-node-boson)
* [**Setting up a boson super node by the community**](broken-reference/)
