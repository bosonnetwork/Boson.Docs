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

# Overview

## Rising the New Carrier

The new Carrier maintains its decentralized nature and the peer-to-peer (P2P) encrypted communication feature from its legacy version 1.0. As part of its evolution, it has been restructured as a layered and permissionless communication network. This decision was made to offer more possibilities for dApp adoption beyond the secure P2P communication feature. The layered structure is listed below, from the bottom up:

* **UDP/TCP**
* [**Kademia DHT**](carrier-dht.md)
* [**Carrier Protocol**](carrier-protocol/)
* [**Carrier Service**](carrier-services/)
* **Applications**

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>A layered and permission-less peer-to-peer encrypted carrier network</p></figcaption></figure>

In this layered structure, the bottom layer consists of core communication protocols UDP/TCP used for sending messages. **Kademia DHT** is a distributed hash table used for decentralized peer-to-peer network, where the network structure is designed to exchange information through nodes. The layer **Carrier Protocol** defines a suite of network protocols between nodes to communicate for applications, while the layer **Carrier Service** contains a serial of system level services serving applications, such as Active Proxy, DHT Proxy, messaging, and public dStore.

Overall, the layered structure offers the network greater scalability and flexibility in terms of application adoption, and also enables more efficient communication between devices, since each layer serves a specific purpose for applications.

## Understand the Carrier Stack

After obtaining an overview of the layered structure of the carrier network, the subsequent step is to delve into the concepts and technologies of each layer. In the following chapters, the main layers - Protocol, and Services - will be described in detail, with a focus on each layer individually.

* [**Carrier Protocol**](carrier-protocol/)
* [**Carrier Services**](carrier-services/)

Once you have gained knowledge of the basic concepts, it is recommended that you reinforce that knowledge through practice. Below are some useful tasks that you can start practicing:

* [**Deploy a Carrier super node**](practices/setting-up-carrier-super-node.md)
* [**Utilize the ActiveProxy service to run a local service**](practices/walk-through-active-proxy-service.md)
* [**Practice using Carrier by following the recommended steps**](practices/practice-in-shell.md)

Here are links to related concepts that can provide you with a deeper understanding of the topic at hand. We hope that they can help you gain a more thorough and nuanced understanding of the technologies involved:

* Carrier Nodes
* Lookup Nodes
* Announce Peers
* Store Values
* DHT Proxy
* Active Proxy
* Messaging service
* dStore service
