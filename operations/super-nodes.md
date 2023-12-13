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
We expect the community to deploy public super nodes and improve the boson network to be more healthy and robust. Please inform us once you start working on this.
{% endhint %}

## Boson Super Nodes

A boson super node, also known as a bootstrap node, is a special type of boson node dedicated to helping new nodes join the boson network. It achieves this by propagating nodes into the routing tables of neighboring nodes, and keeping the routing tables of neighboring nodes healthy and robust. Since super nodes serve as bootstrap node, they must run on a VPS with a public IP address.

In addition to serving as bootstrap nodes, boson super nodes also offer built-in services such as Web Gateway and Active Proxy services. More built-in services will be integrated as the development of the network progresses.

## A Set of Super Nodes Running as Bootstrap Nodes

When the Trinity-Tech team finished the initial version of boson implementation, they deployed a set of public boson super nodes with Active Proxy support. This set contains a total of 8 public nodes, forming the very first Boson network.

In the initial version, each boson super node is running with the Active Proxy service. The Active Proxy service can be leveraged by a personal microservice that was originally only allowed for access within LAN, but can now be accessed by the public. Additionally, users can register a PC2 name from the website [https://pc2.net](https://pc2.net/) provided by Trinity-Tech to bind the user service.

Here is the initial list of public super nodes deployed by the **trinity-tech** team\*\*:\*\*

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
    "address": "66.42.74.13", 
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

When the community decides to set up a super node for public or experimental usage, a proper configuration file is required. This file should include a few super nodes as bootstrap nodes to connect with. After the super node is running, it will automatically connect to the Boson network gradually through these bootstrap nodes.

Here is an example config file without for the community to use with a few super nodes deployed by **trinity-tech**. We are pleased to see more public super nodes from the community.

```json
{
  "ipv4": true,
  "ipv6": false,
  "port": 39001,
  "dataDir": "/var/lib/boson",

  "bootstraps": [
    {
      "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ",
      "address": "155.138.245.211",
      "port": 39001
    },
    {
      "id": "4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41",
      "address": "66.42.74.13",
      "port": 39001
    }
  ],
  "services": [
    {
      "class": "io.bosonnetwork.service.dhtproxy.DHTProxy",
      "configuration": {
        "port": 8088
      }
    },
    {
      "class": "io.bosonnetwork.service.activeproxy.ActiveProxy",
      "configuration": {
        "port": 8090,
        "portMappingRange": "20000-22000",
        "connections":8,
        "maxConnections":64,
        "peerPrivateKey": "YOUR-PRIVATE-KEY-TO-PEER"
      } 
    }
  ]  
}
```

## More Links

* [Boson Super Nodes](super-nodes.md#boson-super-nodes)
* [Setting up a Boson super node by the community](broken-reference)
* [Java SDK API document](../developer-kits/java.md)
