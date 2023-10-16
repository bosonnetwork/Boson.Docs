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

# Super Nodes

{% hint style="info" %}
We expect the community to deploy public super nodes and improve the carrier network to be more healthy and robust. Please inform us once you start working on this.
{% endhint %}

## Carrier Super Nodes

A carrier super node, also known as a bootstrap node, is a special type of carrier node dedicated to helping new nodes join the carrier network. It achieves this by propagating nodes into the routing tables of neighboring carrier nodes, and keeping the routing tables of neighboring nodes healthy and robust. Since carrier super nodes serve as bootstrap node, they must run on a VPS with a public IP address.

In addition to serving as bootstrap nodes, carrier super nodes also offer built-in services such as DHT Proxy and Active Proxy services. More built-in services will be integrated as the development of the carrier network progresses.

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>An imagined carrier network consists of Super Nodes, Regular Nodes, and dApp adoptions.</p></figcaption></figure>

## A Set of Super Nodes Running as Bootstrap Nodes

When the Trinity-Tech team finished the initial version of carrier implementation, they deployed a set of public carrier super nodes with Active Proxy support. This set contains a total of 8 public nodes, forming the very first Carrier network.

In the initial version, each carrier super node is running with the Active Proxy service. The Active Proxy service can be leveraged by a personal microservice that was originally only allowed for access within LAN, but can now be accessed by the public. Additionally, users can register a PC2 name from the website [https://pc2.net](https://pc2.net/) provided by Trinity-Tech to bind the user service.

Here is the initial list of public super nodes deployed by the **trinity-tech** team**:**

```json
{ 
    "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ", 
    "address": "155.138.245.211", 
    "port": 39001
},
{ 
    "id": "6o6LkHgLyD5sYyW9iN5LNRYnUoX29jiYauQ5cDjhCpWQ", 
    "address": "45.32.138.246", 
    "port": 39001
},
{ 
    "id": "8grFdb2f6LLJajHwARvXC95y73WXEanNS1rbBAZYbC5L", 
    "address": "140.82.57.197", 
    "port": 39001
},
{ 
    "id": "4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41", 
    "address": "107.191.62.45", 
    "port": 39001
},
{ 
    "id": "5BJ8SZZQ4z4izhw82W2ksyuTCQz3GwWUWBSaza4qzVT9", 
    "address": "207.148.82.19", 
    "port": 39001
},
{ 
    "id": "8fAHSUAtKmVycxQK2VRDnhcSL1XX9ciweULt4dHx6Yfg", 
    "address": "140.82.34.87", 
    "port": 39001
},
{ 
    "id": "J44cKHHjJzpJJhM4tqwZxYhv9Cynozx38xeR2WcvfFRN", 
    "address": "139.84.232.184", 
    "port": 39001
}
```

## A Config Example for the Super Node

When the community decides to set up a super node for public or experimental usage, a proper configuration file is required. This file should include a few super nodes as bootstrap nodes to connect with. After the super node is running, it will automatically connect to the Carrier network gradually through these bootstrap nodes.

Here is an example config file without for the community to use with a few super nodes deployed by **trinity-tech**. We are pleased to see more public super nodes from the community.

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39001,
  "dataDir": "/var/lib/carrier",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    },
    {
      "id": "4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41",
      "address": "107.191.62.45",
      "port": 39001
    }
  ],
  "services": [
    {
      "class": "elastos.carrier.service.dhtproxy.DHTProxy",
      "configuration": {
        "port": 8088
      }
    },
    {
      "class": "elastos.carrier.service.activeproxy.ActiveProxy",
      "configuration": {
        "port": 8090,
        "portMappingRange": "20000-22000",
        "peerPrivateKey": "YOUR-PRIVATE-KEY-TO-PEER"
      } 
    }
  ]  
}
```

## More Links

* [Carrier Super Nodes](super-nodes.md#carrier-super-nodes)
* [Setting up a Carrier super node by the community](../getting-started/practices/deploying-super-node.md)
* [Java SDK API document](../developer-kits/java.md)
