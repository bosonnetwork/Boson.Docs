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

# Nodes

The Boson Network encompasses all nodes worldwide, categorized based on their deployment on public VPS, personal devices, Raspberry Pi devices, browsers, and other platforms. Together, these nodes form the integral components of the entire network.

* [**Super Node ( boson node)**](nodes.md#super-node-boson-node)
* [**Native Node (photon node)**](nodes.md#native-node-photon-node)
* [**Lite Node (gluton node)**](nodes.md#lite-node-gluton-node)

<figure><img src="../../.gitbook/assets/boson-nodes-topology.png" alt=""><figcaption><p>The Boson Network being composed of three types of nodes.</p></figcaption></figure>

### Super Node - <mark style="color:green;">boson node</mark>

A boson super node is a specialized node dedicated to assisting new nodes seeking to join the network and broadcasting their presence. As public node services catering to applications, super nodes necessitate a VPS server with a public IP address. This is crucial to ensure that the public services they offer remain accessible, avoiding potential connectivity issues that may arise if the Super Node is running within a home WiFi network.

### Native Node - <mark style="color:green;">photon node</mark>

A native node typically is running alongside an application or is seamlessly integrated into an application on desktops or devices. Applications can leverage boson nodes for various purposes, such as interacting with others to store or locate values, announcing or discovering peers, or directly streaming traffic. Native nodes commonly operate within a home WiFi network and initiate their network connection by bootstrapping from the super node during their initial connection. Once connected, these nodes autonomously organize themselves and propagate their presence throughout the network.

### Lite Node - <mark style="color:green;">gluton node</mark>

A lite node is crafted to operate as a browser application, leveraging the Web Gateway service provided by a designated super node. Unlike native nodes, lite nodes do not function independently but rather communicate with other nodes through the super node, facilitated by the web gateway service. Consequently, web applications running in the browser can be perceived as lite DHT nodes in terms of their interactions with other nodes.
