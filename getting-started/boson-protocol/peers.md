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

# Peers

As an integral component of the Kademlia DHT network, the boson network functions as a highly reliable and scalable platform for publishing and subscribing peers, which are mostly referred as service peers. Peers are instantiated by encapsulating entries for specific services operated as daemons, facilitating public accessibility across the network. Each service peer is identified by a unique ID within the same namespace as node IDs. Adhering to the design of the DHT algorithm, peer entities are published across the network and stored on nodes with IDs neighboring the corresponding value ID.

Each Peer is endowed with a signing key pair and comprises an access entry node, a service port, and a signature proof. The public key functions as the Peer ID, while the private signing key generates the signature based on the node ID and port. Recipients can verify the signature to authenticate the integrity and ownership of this service peer. The access entry node facilitates the retrieval of the IPv4 or IPv6 address for the service peer, as it shares the same IP address as the node.

## Service Publishing and Subscribing&#x20;

In the boson network, the two primitive protocols: **`announce_peer`** and **`find_peer`** are used to publish and subscribe the service peer over the network. When a new peer entity is created, it is distributed to the nodes with neighboring IDs to the peer ID using announce\_peer protocol. Upon receiving the peer, the recipient node caches it in the local database storage. Cached peers in nodes may expire after 2 hours unless periodically rebroadcasted.&#x20;

An application can employ the find\_peer protocol to lookup the peer and subscribe it using a specified peer ID. It is crucial to note that the peer ID should be obtained through an alternative method not involving the boson network.
