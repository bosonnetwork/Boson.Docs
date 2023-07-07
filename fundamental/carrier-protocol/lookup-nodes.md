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

# Lookup Nodes

## Carrier Nodes

Carrier is a fully decentralized communication network that consists of carrier nodes running worldwide. These nodes are categorized into the different types based on the way they contribute to the network:

* [**Carrier Super Node**](lookup-nodes.md#carrier-super-node)
* **Carrier Native Node**
* **Carrier Lite Node**

#### Carrier Super Node

A super node is a dedicated carrier node that serves new carrier nodes looking to join the network and broadcast their appearance. It also provides carrier services for applications like DHT Proxy, Active Proxy, and later, Messaging and public dStore.

Since super nodes are public node services that offer system services to applications, they require a VPS server with a public IP address. Otherwise, the public services they offer may not be accessible from the super node if it's running under a home WiFi network.

The community is encouraged to deploy and run their own Carrier super nodes for public use. The more super nodes that run on the network, the greater the benefit for improving the reliability and decentralization of the Carrier network. Currently, there is no enforced economic model for running a Carrier super node, but the possibility of an incentive mechanism is under consideration.

#### Carrier Native Node

A native node generally runs alongside an application or is integrated into the application to fulfill its features for end-users.

Finally, a carrier crawler is essentially a native node dedicated to crawling all active nodes in the entire carrier network.

#### Carrier Lite Node

A lite node is intended to run on a browser to use the DHT Proxy service from a specific super node



## Protocol - find\_node

## More Links
