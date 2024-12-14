Static NAT with VRF

*** CORE ***

1.) Assign IPs to upstream (toward EDGE router) and downstream (toward hosts) interfaces.

2.) Activate BGP: assign Router-ID, configure EDGE router interface as neighbor (different AS, this is eBGP), configure address-family ipv4 to redistribute connected subnets, activate neighbor.

3.) Configure a default route that points to the neighbor interface as the next hop.

*** EDGE ***

1.) Create a VRF with an RD that contains the AS # of the BGP.

2.) Designate link to CORE router to perform 'ip vrf forwarding (VRF)'

3.) Assign IP address and 'ip nat inside' to link to CORE router

4.) Give public IP to link that faces EXTERNAL router. Designate that link as 'ip nat outside'.

5.) Create a default route (Global routing table) that points to the IP address on the EXTERNAL router link.

6.) Create a default route (VRF routing table) that points to the IP address on the EXTERNAL router link, specify 'global' at end of route.

7.) Create BGP process, Router-ID, and configure CORE router as neighbor (different AS, this is eBGP), configure address-family ipv4 vrf VRF, activate neighbor.

8.) Define static NAT 'ip nat inside source static PRIVATE HOST IP PUBLIC GLOBAL IP vrf VRF'

*** EXTERNAL ***

1.) Define IPs on both the link that faces EDGE (Public IP) and link that faces the host (Private IP)

2.) Create a static route for the remote host network with a next hop of the EDGE router interface that is connected to
the EXTERNAL router.

![image description](relative/path/in/repository/to/image.svg)
