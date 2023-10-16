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

# Active Proxy

The **Active Proxy** service is the first add-on service provided by **Carrier Super Nodes**. It allows a local service running on your home WiFi to be announced on a set of carrier super nodes. Once the service is announced on carrier super nodes, it can be accessed by the public naturally.

## The Use Cases Could Benefit From Active Proxy

Suppose you want to run a blog service on a Raspberry device in your home WiFi and share stories on the blog service with the public. In this case, you can use the **Active Proxy** from the super nodes you trust the most to announce your blog service to the public.

Another example is when you have deployed a NAS or personal storage service on your home WiFi. It works to access your data from the service at your home, but if you need to access your personal data from outside, you can use **Active Proxy** to announce the service access point from home WiFi to the internet while still keeping the privacy of your data.

<figure><img src="../../.gitbook/assets/gateway-service.png" alt=""><figcaption><p>An Imagined Gateway Service Leveraging on Active Proxy Feature</p></figcaption></figure>

## Why Do You Need Active Proxy for Local Services?

If a local service is running on a home WiFi, it can only be accessed within the LAN and not by external users. This is because the NAT mechanism blocks initial access directly from the public network. To allow external access, users can either run services on a VPS with a public IP address or leverage third-party DDNS services to publish the service.

In the carrier network, each carrier super node runs an **Active Proxy** service. Any user can choose a set of the super nodes to announce a service entry, making the service accessible for the public.

## How Does Active Proxy Work

A complete **Active Proxy** service consists of client and server services. The Carrier super node hosts the server part, while the Carrier regular node, running alongside a user's service, hosts the client part.

By using a config file to specify the active proxy peer ID, a regular Carrier node hosting an active proxy client will initiate a dedicated connection with the specified Carrier super node. Once the connection is established, it will be used to forward traffic between external dApps and the user's internal service.

Assuming that the connection between an external dApp and a user service deployed on a home WiFi has been established, and the dApp requests access to the user service. The request from the dApp is forwarded to the internal carrier regular node on the user's home WiFi via an active proxy server running on a super node. The active proxy client in the regular node then forwards the traffic to the target user service. The response is then forwarded in reverse from the internal carrier regular node to the super node outside.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>The work flow for Active Proxy between dApp and the user service.</p></figcaption></figure>

