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

# Carrier Protocols

## Kademlia DHT

Kademlia DHT is a distributed hash table designed for decentralized peer-to-peer networks by Petar Maymounkov and David Mazières in 2002. It specifies the structure of the network and the exchange of information through node lookups. Kademlia DHT nodes communicate with each other using UDP. Each DHT node is identified by a node ID, and the Kademlia algorithm uses this ID to locate other nodes or values. You can learn more about Kademlia DHT on [Wikipedia](https://en.wikipedia.org/wiki/Kademlia).

The distributed nature of Kademia requires each node to maintain a mapping of a subset of the nodes on the network in its own routing table. This feature makes the network highly resistant to denial-of-service attacks and the loss of a group of nodes, as the protocol simply routes around the unavailable nodes. Therefore, it creates resilience against attacks, downtime, and central points of failure.

Due to the aforementioned advantages, Kademia DHT has been widely used in projects such as Bittorrent, Ethereum, IPFS, and Swarm. Carrier has also decided to integrate it as the underlying DHT network so that Carrier can be a fully decentralized, reliable communication platform.

## Carrier Protocols

* ping&#x20;
* find\_node
* announce\_peer
* find\_peer
* store\_value
* find\_value

## Related Links:

* [**Carrier Nodes**](carrier-node.md)
* [**Carrier Peer**](carrier-peer.md)
* [**Carrier Value**](carrier-value.md)
