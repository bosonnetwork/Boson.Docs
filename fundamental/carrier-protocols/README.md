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

Kademlia DHT is a distrbuted hash table for decentralized peer-to-peer network desgined by Petar Maymounkov and David Mazières in 2002. It specifes the structure of the network and the exchange of information through node lookups. Kademlia DHT nodes communcate among themselves using UDP.  Each DHT node is identified by a number or node ID, and the Kademlia algorithm uses the node ID to locate nodes or values.  Learn more on [Kademlia DHT wikipedia](https://en.wikipedia.org/wiki/Kademlia) website.

The distributed nature of kademia means each node must keep the mapping of a subset of the nodes on the network in it's own routing table, which makes the network highly resistant to denial of service attacks and the loss of a group of nodes as the protocol simply routes around the unavailable nodes. Therefore, it creates resislicency agains attack, downtime and central points of failure.

## Supported Protocols

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
