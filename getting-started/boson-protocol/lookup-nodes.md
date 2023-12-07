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

## Boson Node

Boson is a fully decentralized communication network that consists of boson nodes running worldwide. These nodes are categorized into the different types based on the way they contribute to the network:

* [**Boson Super Node**](lookup-nodes.md#boson-super-node)
* [**Boson Native Node**](lookup-nodes.md#boson-native-node)
* [**Boson Lite Node**](lookup-nodes.md#boson-lite-node)

## Boson Super Node

A **boson super node** is a dedicated node that serves new nodes looking to join the network and broadcast their appearance. It's also running to provides services for applications like Web Gateway, Active Proxy, and later, Messaging and dStore.

Since super nodes are public node services that offer services to applications, they require a VPS server with a public IP address. Otherwise, the public services they offer may not be accessible from the super node if it's running under a home WiFi network.

The community can check the [Boson Java](https://github.com/bosonnetwork/Boson.Java) repository and deploy their own Boson super nodes for public use. The more super nodes running on the network, the greater the benefits for improving the reliability and decentralization of the network. Currently, there is no enforced economic model for running a super node, but the possibility of an incentive mechanism is under consideration.

## Boson Native Node

A native node typically runs alongside an application or is integrated into an application that runs on computers or devices. Applications can use boson nodes to interact with others to store or find values, announce or find peers, or stream traffic directly. Native nodes can run under a home WiFi network and join the network by bootstrapping from the super node the first time they connect. Once connected to the network, they organize themselves and propagate their appearance on the network.

Developers can check the SDK APIs and manage to integrate the Boson SDK to fulfill the needs of their applications.

One special case worth mentioning is that a boson crawler can be essentially considered as a native node. However, it is dedicated to crawling all active nodes in the entire network. The results collected can then be presented on a Boson Explorer to actively showcase the topology of the Boson network.

## Boson Lite Node

A lite node is designed to run as a browser application, utilizing the Web Gateway service from a specific super node. Essentially, lite nodes are not DHT nodes themselves, but communicate with other nodes through the super node with the assistance of the web gateway service. Therefore, web applications running in the browser can still be considered lightweight DHT nodes from the perspective of interacting nodes.

## Protocol - find\_node

## More Links

* Web Gateway
* Active Proxy
* Messaging 
* dStore

## Categories of Boson Nodes

The boson network comprises all the nodes running worldwide, including the following types of nodes running on public VPS, personal devices, Raspberry Pi devices, or even browsers and so on:

* [**Boson Super node**](lookup-nodes.md#boson-super-node)
* [**Boson Native node**](lookup-nodes.md#boson-regular-node)
* [**Boson Lite Node**](lookup-nodes.md#boson-light-node)

In brief, a super node is required to run on a VPS server with a public address to bootstrap new nodes joining the network. A native node generally runs alongside an application or is integrated into the application to fulfill its features for end-users. A lite node is intended to run on a browser to use the web gateway service from a specific super node.

Each category of boson nodes serves its own purpose and contributes its traffic to boost the security and health of the network.
