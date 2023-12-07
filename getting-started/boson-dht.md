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

# Boson DHT

## Kademlia DHT

Kademlia DHT, created by Petar Maymounkov and David Mazières in 2002, is a distributed hash table specifically designed for decentralized peer-to-peer networks. It defines the network structure and outlines the process of exchanging information through node lookups. Communication between Kademlia nodes is facilitated using UDP. Each DHT node is uniquely identified by a node ID, a crucial element employed by the Kademlia algorithm to locate other nodes or values. For a more in-depth exploration of Kademlia DHT, you can refer to the dedicated [Wikipedia page](https://en.wikipedia.org/wiki/Kademlia).

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

The distributed nature of Kademlia necessitates each node to maintain a mapping of a subset of nodes on the network within its routing table. This intrinsic feature endows the network with high resistance to denial-of-service attacks and mitigates the impact of node loss, as the protocol dynamically reroutes around unavailable nodes. This resilience fortifies the network against potential attacks, downtimes, and central points of failure.

Capitalizing on these advantages, Kademlia DHT has found widespread application in notable projects like Bittorrent, Ethereum, IPFS, and Swarm. Recognizing its efficacy, Boson has chosen to integrate Kademlia as the underlying DHT network, aligning with the vision of establishing Boson as a fully decentralized and reliable communication platform.

## The Boson Network

The Boson Network stands as a fully decentralized, peer-to-peer encrypted communication platform, employing Kademlia DHT as its foundational network infrastructure. A comprehensive suite of protocols has been meticulously implemented to foster seamless communication among nodes. These protocols encompass the addressing and propagation of nodes, values, and peer entities through the entire Network. The following is a compilation of primitive protocols outlined in the initial standard specification supported:

* ping
* find\_node
* store\_value
* find\_value
* announce\_peer
* find\_peer
