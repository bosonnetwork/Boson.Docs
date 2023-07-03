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

# ⛷ Super Nodes

## Carrier Super Nodes

A carrier super node, also known as a bootstrap node, is a special type of carrier node dedicated to helping new nodes join the carrier network. It achieves this by propagating nodes into the routing tables of neighboring carrier nodes, and keeping the routing tables of neighboring nodes healthy and robust. Since carrier super nodes serve as bootstrap node, they must run on a VPS with a public IP address.

In addition to serving as bootstrap nodes, carrier super nodes also offer built-in services such as DHT Proxy and Active Proxy services. More built-in services will be integrated as the development of the carrier network progresses.

## A Set of Super Nodes Running as Bootstrap Nodes

Since the Trinity-Tech team finished the initial version of the carrier network implementation, they deployed a set of carrier super nodes. This set contained a total of 8 super nodes, forming the very first version of the Carrier network.

In the initial version, each carrier super node runs the Active Proxy service. Users can use this service to set up a user service under home WiFi, which can then be forwarded onto carrier super nodes for public access. Additionally, users can utilize the cutting-edge website [https://pc2.net](https://pc2.net/) or [http://pc2.org](http://pc2.org/) provided by Trinity-Tech to bind the user service and assign a DDNS name for forwarding.

## The set of super nodes used by pc2.net

{% tabs %}
{% tab title="Super Node1" %}
```json
{ 
    "id": "HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ", 
    "address": "carrier1.trinity-tech.io", 
    "port": 39001 
}
```
{% endtab %}

{% tab title="Super Node2" %}
```json
{ 
    "id": "6o6LkHgLyD5sYyW9iN5LNRYnUoX29jiYauQ5cDjhCpWQ", 
    "address": "carrier2.trinity-tech.io", 
    "port": 39001 
    
 }
```
{% endtab %}

{% tab title="Super Node3" %}
```json
{ 
    "id": "8grFdb2f6LLJajHwARvXC95y73WXEanNS1rbBAZYbC5L", 
    "address": "carrier3.trinity-tech.io", 
    "port": 39001 
}
```
{% endtab %}

{% tab title="Super Node4" %}
```json
{ 
    "id": "4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41", 
    "address": "107.191.62.45", 
    "port": 39001 
}
```
{% endtab %}
{% endtabs %}

## The set of super nodes used by pc2.org

{% tabs %}
{% tab title="Super Node5" %}
```json
{ 
    "id": "5BJ8SZZQ4z4izhw82W2ksyuTCQz3GwWUWBSaza4qzVT9", 
    "address": "207.148.82.19", 
    "port": 39001 
}
```
{% endtab %}

{% tab title="Super Node6" %}
```json
{ 
    "id": "8fAHSUAtKmVycxQK2VRDnhcSL1XX9ciweULt4dHx6Yfg", 
    "address": "140.82.34.87", 
    "port": 39001 
}
```
{% endtab %}

{% tab title="Super Node7" %}
```json
{ 
    "id": "J44cKHHjJzpJJhM4tqwZxYhv9Cynozx38xeR2WcvfFRN", 
    "address": "139.84.232.184", 
    "port": 39001
}
```
{% endtab %}

{% tab title="Super Node8" %}
```json
```
{% endtab %}
{% endtabs %}
