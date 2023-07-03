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

# ⭕ Active Proxy

The **Active Proxy** service is the first add-on service provided by carrier super nodes. It allows a local service running on your home WIFI to be announced on a set of carrier super nodes. Once the service is announced on carrier super nodes, it can be accessed by the public naturally.

## The Use Cases Could Benefit From Proxy Active

Suppose you want to run a blog service on a Raspberry device in your home WIFI and share stories on the blog service with the public. In this case, you can use the **Active Proxy** from the super nodes you trust the most to announce your blog service to the public.

Another example is when you have deployed a NAS or personal storage service on your home WIFI. It works to access your data from the service at your home, but if you need to access your personal data from outside, you can use **Active Proxy** to announce the service access point from home WIFI to the internet while still keeping the privacy of your data.

## Why Do You Need Active Proxy for Local Services?

If a local service is running on a home WIFI, it can only be accessed within the LAN and not by external users. This is because the NAT mechanism blocks initial access directly from the public network. To allow external access, users can either run services on a VPS with a public IP address or leverage third-party DDNS services to publish the service.

In the carrier network, each carrier super node runs an **Active Proxy** service. Any user can choose a set of the super nodes to announce a service entry, making the service accessible for the public.

## How Does ActiveProxy Work

TODO

