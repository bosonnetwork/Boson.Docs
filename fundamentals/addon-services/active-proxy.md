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

# ⭕ Active proxy

The **ActiveProxy** service is the first add-on service provided by the **carrier super node**. It is used to announce a local service on the carrier super node, while the local service is running at your home LAN. Once the service is announced on the specific carrier node, this service can be accessed by the public naturally.

## The usecases could benefit from ProxyActive serivce

Imagine the case that you want to run a blog service on Raspbery deivce at your home LAN, and want to the stories on blog service to be shared with the public.  Then you can leverage the **ActiveProxy** from the super node you trust the most to publish your blog service to the public.

Another natural case is that you have deployed a NAS or psersonal storage service on your home LAN. It's working to access your data from the service service under your home, but once you need to access or upate your personal data from outside, you can leverage **ActiveProxy** to move the service access point from LAN to internet, but still keep the privacy to your data.

## Why do you need ActiveProxy for local service

Generally, if a local service is running on a home LAN, it can only be accessed within the LAN and not by external users. This is due to the NAT mechanism blocking initial access directly from the public network. To allow external access, users can run services on a VPS with a public IP address or leverage third-party DDNS services to publish the service.

In a carrier network, each carrier super node runs an Active Proxy service. Any user can choose one of the super nodes to announce a service entry on the super node, making the service accessible to the public.

## How does ActiveProxy work

TODO

