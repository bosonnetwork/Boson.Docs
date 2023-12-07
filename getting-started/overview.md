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

## Rising the New Boson

The updated Boson retains its decentralized essence and preserves the  peer-to-peer (P2P) encrypted communication feature from its inception.  Evolving with a strategic restructuring, it now operates as a layered  and permissionless communication network. This transformation aims to  broaden the spectrum of potential applications beyond the secure P2P  communication feature. The layered structure, presented from the bottom  up, is as follows:

* **UDP/TCP**
* [**Kademia DHT**](boson-dht.md)
* [**Boson Protocol**](boson-protocol/)
* [**Boson Service**](boson-services/)
* **Applications**

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>A layered and permission-less peer-to-peer encrypted network</p></figcaption></figure>

In this layered structure, it's composed of core communication protocols UDP/TCP, facilitating the transmission of messages. The Kademia DHT occupies the subsequent layer, serving as a distributed hash table for decentralized peer-to-peer networking. This layer is intricately designed to facilitate information exchange among nodes. Moving up, the Boson Protocol layer encompasses a suite of network protocols enabling communication between nodes for various applications. The topmost layer, Boson Service, encompasses a series of system-level services designed to cater to applications. These services include the Web Gateway, Active Proxy, Messaging, and dStore.

Overall, the layered structure offers the network greater scalability and flexibility in terms of application adoption, and also enables more efficient communication between devices, since each layer serves a distinct purpose for applications.

## Understand the Stack

Having gained an overview of the layered structure of the network, the next step is to delve into the intricacies of each layer's concepts and technologies. In the upcoming chapters, the primary layers, namely Protocol and Services, will be meticulously examined. The focus will be on providing a detailed understanding of each layer individually.

* [**Boson Protocol**](boson-protocol/)
* [**Boson Services**](boson-services/)

Once you have acquired a foundational understanding of the basic concepts, it is advisable to solidify and reinforce that knowledge through practical application. Below, you will find a set of beneficial tasks that serve as valuable exercises to enhance your proficiency:

* [**Deploy a Boson super node**](practices/deploying-super-node.md)
* [**Utilize the ActiveProxy service to run a local service**](practices/leveraging-active-proxy-service.md)
* [**Practice using Boson by following the recommended steps**](practices/the-interactive-shell-command.md)

Explore the following links to delve deeper into related concepts, offering a comprehensive understanding of the topic at hand. These resources aim to enrich your knowledge, providing a more thorough and nuanced insight into the technologies involved:

* Boson Nodes
* Lookup Nodes
* Announce Peers
* Store Values
* Web Gateway
* Active Proxy
* Messaging
* dStore
