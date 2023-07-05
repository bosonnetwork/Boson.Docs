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

# 🎏 Architecture

## A Layered, Permission-less Communication Platform

The new Carrier maintains its decentralized nature and secure peer-to-peer (P2P) communication feature from version 1.0. However, it has been restructured as a layered, open, and permission-less platform. This decision was made to offer more possibilities for dApp adoption beyond the secure P2P communication feature.  The layered structure is listed below, from the bottom up:

* **UDP/TCP**
* **Kademia DHT (Distributed Hash Table)**
* **Carrier Protocol**
* **Carrier Service**
* **Applications**

In this layered structure, the bottom layer consists of core communication protocols UDP/TCP from the internet protocol suite, which are used to send messages. The **Kademia DHT** is a distributed hash table used for decentralized peer-to-peer networks, and the network structure is designed to exchange information through nodes using the UDP protocol. The **Carrier Protocol** layer defines the network protocols among nodes to provide a platform for applications, while the **Carrier Service** layer contains multiple system services such as Active Proxy, DHT Proxy, messaging, and public dStore for application adoption.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>A layered, open and permission-less Carrier Network</p></figcaption></figure>



Being a layered communication network, it means that the network will allows for more efficient communication between devices, and each layer serves a specific purpose of applications. Additionally, this structure allows for greater scalability and flexibility. Overal, the layered desgin of Carrier network is one of it's key strengths, enable it provide fast, secure and reliable communication for users all round the world.

## Categories of Carrier Nodes

The carrier network comprises all the carrier nodes running worldwide, including the following types of nodes running on public VPS, personal devices, Raspberry Pi devices, or even browsers and so on:

* [**Carrier Super node**](architecture.md#carrier-super-node)
* [**Carrier Native node**](architecture.md#carrier-regular-node)
* [**Carrier Lite Node**](architecture.md#carrier-light-node)
* [**Carrier Crawler**](architecture.md#carrier-crawler)

In brief, a super node is required to run on a VPS server with a public address to bootstrap new carrier nodes joining the network. A native node generally runs alongside an application or is integrated into the application to fulfill its features for end-users. A lite node is intended to run on a browser to use the DHT Proxy service from a specific super node. Finally, a carrier crawler is essentially a native node dedicated to crawling all active nodes in the entire carrier network.

Each category of carrier nodes serves its own purpose and contributes its traffic to boost the security and health of the Carrier network.

## More Links

* Carrier Protocols
* Carrier Services
* Active Proxy
* DHT Proxy
* Message services
* Public dStore&#x20;

