** Next-Hop-Self **

![image description](https://raw.githubusercontent.com/ViggoMode2021/Border-Gateway-Protocol/refs/heads/main/Next-Hop-Self/Topology.png)

Overview: BGP routers show the next hop as the router that advertised the network, which can cause connectivity issues between iBGP and eBGP routers. Specifying 'next-hop-self' allows routers to send the proper next hop, in order to create an adequate path to a remote network in a different AS.
