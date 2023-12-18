# Peers

As part of the Kademlia DHT network, the Boson Network not only features an efficient routing and lookup mechanism but also operates as a highly reliable and scalable platform for peer retrieval and service discovery. Peers are instantiated by encapsulating entries for specific services run by users, thereby enabling public accessibility across the network. Each peer is assigned a unique ID within the same namespace as node IDs. Following the design of the DHT algorithm, peer entities are announced over the network and stored on nodes with IDs neighboring the corresponding value ID.

Every Peer entity is equipped with a signing key pair and contains an access entry node, a service port, and a signature proof. The public key serves as the Peer ID, while the private signing key generates the signature based on the node ID and port. Recipients can authenticate the integrity and ownership of this service peer by verifying the signature. The access entry node facilitates the retrieval of the IPv4 or IPv6 address for the service peer, as it shares the same IP address as the node.

