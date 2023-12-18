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

The boson network encompasses all nodes worldwide, categorized based on their deployment on public servers, personal devices, Raspberry Pi devices, browsers, and other platforms. Together, these nodes form the integral components of the entire network.

* [**Super Node - Boson**](nodes.md#super-node-boson-node)
* [**Native Node - Photon**](nodes.md#native-node-photon-node)
* [**Lite Node - Gluton**](nodes.md#lite-node-gluton-node)

<figure><img src="../../.gitbook/assets/boson-nodes-topology.png" alt=""><figcaption><p>The Boson Network being composed of three types of nodes.</p></figcaption></figure>

### Super Node

A super node, marked as a boson node, is a bootstrap node dedicated to assisting new nodes seeking to join the network and broadcasting their presence. As public node services catering to applications, super nodes necessitate a server with public IP address. This is crucial to ensure that the public services they offer remain accessible, avoiding potential connectivity issues that may arise if the super node is running within a home-based network.

### Native Node

A native or regular node, marked as a photon node, typically is running alongside an application or is seamlessly integrated into an application on desktops or devices. Applications can leverage native nodes for various purposes, such as interacting with others to store or locate values, announcing or discovering peers, or directly streaming traffic. Native nodes commonly operate within a home-based network and initiate their network connection by bootstrapping from the super node during their initial connection. Once connected, these nodes autonomously organize themselves and propagate their presence throughout the network.

### Lite Node

A lite node, marked as a gluton node, is crafted to operate as a browser application, leveraging the web gateway service provided by a designated super node. Unlike native nodes, lite nodes do not function independently but rather communicate with other nodes through the super node, facilitated by the web gateway service. Consequently, web applications running in the browser can be perceived as lite DHT nodes in terms of their interactions with other nodes.

## Node Propagation and Retrieval

As the boson network operates on the Kademlia DHT protocol, it employs a fundamental protocol named **`find_node`** to disseminate node information among interconnected nodes. This propagation occurs when nodes join the network and periodically thereafter. When a node receives information about neighboring nodes, it algorithmically merges these nodes into its routing table, improving the efficiency of data retrieval and network communication.

Every node in the network is characterized by a unique node ID, a distinctive identifier that sets it apart. Applications can seamlessly look up or retrieve specific node details by utilizing this node ID, which includes the associated IPv4 or IPv6 addresses, along with the version of node.

### Related Links

* [**Kademlia DHT**](../kademlia-dht.md)
* The Protocol - find\_node
