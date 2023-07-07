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

## Carrier Node

Carrier is a fully decentralized communication network that consists of carrier nodes running worldwide. These nodes are categorized into the different types based on the way they contribute to the network:

* [**Carrier Super Node**](lookup-nodes.md#carrier-super-node)
* [**Carrier Native Node**](lookup-nodes.md#carrier-native-node)
* [**Carrier Lite Node**](lookup-nodes.md#carrier-lite-node)

## Carrier Super Node

A **carrier super node** is a dedicated node that serves new nodes looking to join the network and broadcast their appearance. It's also running to provides services for applications like DHT Proxy, Active Proxy, and later, Messaging and public dStore.

Since super nodes are public node services that offer system services to applications, they require a VPS server with a public IP address. Otherwise, the public services they offer may not be accessible from the super node if it's running under a home WiFi network.

The community can check the [Carrier Java](https://github.com/elastos/Elastos.Carrier.Java) repository and deploy their own Carrier super nodes for public use. The more super nodes running on the network, the greater the benefits for improving the reliability and decentralization of the Carrier network. Currently, there is no enforced economic model for running a Carrier super node, but the possibility of an incentive mechanism is under consideration.

## Carrier Native Node

A native node typically runs alongside an application or is integrated into an application that runs on computers or devices. Applications can use carrier nodes to interact with others to store or find values, announce or find peers, or stream traffic directly. Native nodes can run under a home WiFi network and join the Carrier network by bootstrapping from the super node the first time they connect. Once connected to the Carrier network, they organize themselves and propagate their appearance on the network.

There are two versions of Carrier SDKs that can be integrated into applications: **C/C++/ Native** and **Swift/iOS**. Developers can check the SDK APIs and manage to integrate the Carrier SDK to fulfill the needs of their applications.

One special case worth mentioning is that a carrier crawler can be essentially considered as a native node. However, it is dedicated to crawling all active nodes in the entire carrier network. The results collected can then be presented on a Carrier Explorer to actively showcase the topology of the Carrier network.

## Carrier Lite Node

A lite node is designed to run as a browser application, utilizing the DHT Proxy service from a specific super node. Essentially, lite nodes are not DHT nodes themselves, but communicate with other nodes through the super node with the assistance of the DHT Proxy service. Therefore, web applications running in the browser can still be considered lightweight DHT nodes from the perspective of interacting nodes.

## Protocol - find\_node

## More Links

* DHT Proxy
* Active Proxy
* Messaging Service
* Public bStore



## Categories of Carrier Nodes

The carrier network comprises all the carrier nodes running worldwide, including the following types of nodes running on public VPS, personal devices, Raspberry Pi devices, or even browsers and so on:

* [**Carrier Super node**](lookup-nodes.md#carrier-super-node)
* [**Carrier Native node**](lookup-nodes.md#carrier-regular-node)
* [**Carrier Lite Node**](lookup-nodes.md#carrier-light-node)

In brief, a super node is required to run on a VPS server with a public address to bootstrap new carrier nodes joining the network. A native node generally runs alongside an application or is integrated into the application to fulfill its features for end-users. A lite node is intended to run on a browser to use the DHT Proxy service from a specific super node.

Each category of carrier nodes serves its own purpose and contributes its traffic to boost the security and health of the Carrier network.
