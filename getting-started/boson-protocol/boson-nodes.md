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

# Boson Nodes

The Boson Network encompasses all nodes worldwide, categorized based on their deployment on public VPS, personal devices, Raspberry Pi devices, browsers, and other platforms. Together, these nodes form the integral components of the entire network.

* **Super Node**
* **Native Node**
* **Lite Node**

### Boson Super Node

A boson super node is a specialized node dedicated to assisting new nodes seeking to join the network and broadcasting their presence. As public node services catering to applications, super nodes necessitate a VPS server with a public IP address. This is crucial to ensure that the public services they offer remain accessible, avoiding potential connectivity issues that may arise if the Super Node is running within a home WiFi network.

### Boson Native Node

A native node typically is running alongside an application or is seamlessly integrated into an application on desktops or devices. Applications can leverage boson nodes for various purposes, such as interacting with others to store or locate values, announcing or discovering peers, or directly streaming traffic. Native nodes commonly operate within a home WiFi network and initiate their network connection by bootstrapping from the super node during their initial connection. Once connected, these nodes autonomously organize themselves and propagate their presence throughout the network.

### Boson Lite Node

A lite node is crafted to operate as a browser application, leveraging the Web Gateway service provided by a designated super node. Unlike native nodes, lite nodes do not function independently but rather communicate with other nodes through the super node, facilitated by the web gateway service. Consequently, web applications running in the browser can be perceived as lite DHT nodes in terms of their interactions with other nodes.

### More Links

* Web Gateway
* Active Proxy
* Federal Based Messaging
* Decentralized Store
