# **IXP Technical Requirements OIX-1**  

Version 3.2, May 1, 2026 

Questions: ix-group@oix.org

This standard defines the technical requirements for an IXP to be certified by OIX. The purpose of the requirements is to provide publicly available information on what the customer of a certified IXP can expect, and not to describe in detail how the IXP is designed, built or operated. IXPs can comply with the OIX standards to serve different communities with different requirements, from a small single datacenter IXPs serving a local community to a large IXP located in multiple datacenters in a metro area.

The keywords used throughout the document are as defined in RFC 2119\.

The IXP **SHOULD** follow the Best Current Operational Practices for an Internet Exchange, posted at [https://github.com/Open-IX/BCOP](https://github.com/Open-IX/BCOP)

## 

## **Table of Contents**

[IXP Technical Requirements OIX-1](#ixp-technical-requirements-oix-1)
- [Table of Contents](#table-of-contents)
- [Foreward](#foreward)
- [1\. Definitions](#definitions)
- [2\. Services](#services)
  - [2.1. Minimal Service Offering](#minimal-service-offering)
  - [2.1.1. Public Exchange VLAN (IX)](#public-exchange-vlan-\(ix\))
  - [2.2. Additional Service Offering](#additional-service-offering)
    - [2.2.1. Private VLAN (PVLAN)](#private-vlan-\(pvlan\))
    - [2.2.2. Optional Layer 3 Services](#optional-layer-3-services)
  - [2.3. Physical Interface](#physical-interface)
  - [2.4. Traffic Forwarding / Fabric Protection](#traffic-forwarding-/-fabric-protection)
    - [2.4.1. Layer 2](#layer-2)
    - [2.4.2. Layer 3](#layer-3)
  - [2.5. Access Lists](#access-lists)
  - [2.6. Customer Interface](#customer-interface)
  - [2.7. Conforming to MANRS](#conforming-to-manrs)
- [3\. Infrastructure](#infrastructure)
  - [3.1. Switching Platform](#switching-platform)
  - [3.2. IP Address Space](#ip-address-space)
  - [3.3. Route Server](#route-server)
  - [3.4. Topology](#topology)
- [4\. Operations](#operations)
  - [4.1. NOC](#noc)
  - [4.2. Monitoring](#monitoring)
  - [4.3. Statistics](#statistics)
  - [4.4. Website](#website)
  - [4.5. Pricing](#pricing)
  - [4.6. Miscellaneous](#miscellaneous)

## 

## Forward

**Changes:**

- Initial updating to include numbering  
- Minor formatting updates  
- Add optional Layer 3 Services  
- Clarification on Rate Limiting  
- Use of AS Number for Route Server(s)  
- Maximum Pricing Clarification  
- RPKI use in Route Servers


Please feel free to comment and make any suggestions.

Receptfully,

Paul Emmons

ix-group@oix.org  
Chair Standards Committee  
May, 1 2026  

1. ## **Definitions**

OIX Common Definitions \- OIX has created a Glossary of Data Center and Networking Nomenclature ([https://github.com/Open-IX/Standards/blob/main/definitions.md](https://github.com/Open-IX/Standards/blob/main/definitions.md)) containing our definations of an Internet Exchange / Internet Exchange Point as used in this document.

2. ## **Services**

   1. ### **Minimal Service Offering**

   The IXP **MUST** provide the minimum services described below. This also allows the IXP operator to provide additional services, or methods of interconnection.

      1. #### **Public Exchange VLAN (IX)**

      A switch platform which allows any-to-any interconnection. Customer interfaces with Ethernet frames tagged for the public exchange VLAN **MUST** be forwarded in accordance with the traffic rules indicated in this document.

   ### 

   2. ### **Additional Service Offering**

   The IXP **MAY** provide additional services, as long as they are described on a publicly available website of the IXP

      1. #### **Private VLAN (PVLAN)** {#private-vlan-(pvlan)}

      A private switch platform, whereby any two or more parties may consent to interconnect through either the same physical port that delivers their access to the Public Exchange VLAN or alternatively dedicated physical port(s). If a PVLAN service is offered, in case there are exactly two parties in the private VLAN the connection **MUST** be delivered guaranteed congestion free. In case of more than two parties the service **MAY** be provided on a best efforts basis.

      2. #### **Optional Layer 3 Services**

      A routed platform to provide Layer 3 services, that **MAY** be provided on a best efforts basis.

         1. Examples include  
            1. Caching  
            2. Transit	  
            3. Limited Routing such as Google Verified Peering Provider services  
         2. If an AS Number is utilized it **MUST** be a publicly assigned AS Number from an RIR.   
         3. Use of IRR Filters and RPKI validation **SHOULD** be done.   
         4. If the use of BGP Communities for routing decisions / AS path altering or modification are used, they **MUST** be disclosed to the users.		

   3. ### **Physical Interface**

      1. The IXP **MUST** offer IEEE 802.3 Ethernet connectivity on a common switch infrastructure. Service offerings **MAY** be available at any IEEE defined rate, including IEEE 802.3ad or IEEE 802.1AX link aggregation of any of these rates.  
      2. The complete service offering **MUST** be described on a publicly available website. The information provided **MUST** contain: link rate and physical media (copper, fiber and fiber type). The information **SHOULD** describe how each port type is connected to the fabric.  
      3. The IXP  **SHOULD NOT** allow for physical port speed and duplex negotiation.   
      4. The IXP **MUST** protect the IXP fabric from user misconfiguration, broadcast / unknown and multicast storms, and port flapping.  
      5. The IXP **MAY** provide Rate Limiting (packet shaping and / or packet dropping) on a parties port or link aggregation to provide a speed less than the total speed upon the request of the party.

   4. ### **Traffic Forwarding / Fabric Protection**

      1. #### **Layer 2**

         1. The IXP **MUST** forward frames with the following Ethertypes:  
            1. **0x0800 IPv4**  
            2. **0x86dd IPv6**

            Valid frames with Ethertype 0x86dd may be suppressed on the Public Exchange VLAN using snooping, or alternate methods used to implement IPv6 Neighbor Discovery.

            3. **0x0806 ARP** 

            If there is no provision to handle ARP in any other way, the IXP **MUST** forward frames with this ethertype.

         2. If the IXP has reason to limit certain traffic, the IXP **MUST** publish on a publicly available website what traffic is not allowed and or not forwarded on the exchange platform.  
         3. The IXP **SHOULD** apply a MAC address locking mechanism on a customer port:  
            1. The IXP **MUST** make the policy known to the Customers.  
            2. The IXP **MUST** make known to customers the process to update MAC addresses.

      2. #### **Layer 3**

         The IXP **SHOULD** provide a method to ensure that BGP Peering Sessions only originate from the IPv4 and IPv6 Ranges utilized by the IXP.

   5. ### **Access Lists**

      Per interface access lists as described in BCP214 **SHOULD** be implemented on each customer facing port.

   6. ### **Customer Interface**

      The IXP **MUST** provide a clear demarcation point between the IXP services and the customer. This can be either directly on the exchange or via a common demarcation point available to the customer.

   7. ### **Conforming to MANRS**

      The IXP **SHOULD** participate in Mutually Agreed Norms for Routing Security (MANRS) [https://www.manrs.org/](https://www.manrs.org/) and **SHOULD** encourage its customer to participate in MANRS.

## 

3. ## **Infrastructure**

   1. ### **Switching Platform**

      1. The IXP switching platform **MUST** have backplane capacity to sufficiently handle the aggregate traffic of all customer facing ports, without oversubscription. If individual switching elements contain multiple switch fabric modules, the same conditions **MUST** apply during single component failures.  
      2. The IXP **MUST** run any inter-switch links congestion free.  
      3. The IXP **SHOULD** have redundant power feeds fed from discrete sources (A and B) for all exchange infrastructure. If the IXP does not have redundant power feeds on any components, it **MUST** describe where not on a publicly available website.  
      4. If the IXP does not have full path diversity between two discrete switching elements in different physical locations, this **MUST** be described on the IXPs publicly available website.  
      5. The IXP **SHOULD** describe on a publicly available website the switching platform and the redundancy measures implemented to overcome single component failures.  
      6. The IXP **MUST** facilitate “Mitigating the Negative Impact of Maintenance through BGP Session Culling” as described in RFC 8327 for ports on the Public Peering VLAN.

   2. ### **IP Address Space**

      1. In order to be independent of any of the connected parties, the IP space used on the “Public Exchange VLAN” **MUST** be Provider Independent space or other IP space directly assigned by a RIR for the purpose of operating an IXP. This applies to both IPv4 and IPv6. The IXP operator is responsible for obtaining address space from the respective RIR, as well as providing all material for justification, documentation, and applicable fees as required by the RIR.  
      2. IP space used for Optional Layer 3 Services **MUST** be publicly routable from the Global Internet and **SHOULD** appear in the global internet routing table. Use of RFC 1918 space **MUST** not be utilized.
         
   3. ### **Route Server** {#route-server}

      The IXP **SHOULD** offer two route servers to facilitate multilateral peering between the customer on the Public Peering VLAN.   
      1. If a route server service is offered:  
         1. It **MUST** support both IPv4 and IPv6, and 16-bit and 32-bit ASNs.    
         2. The AS number used for the route server implementation **MUST** be a unique AS number assigned by one of the RIRs.    
            1. The AS **MUST** be utilized only for Route Servers  
            2. The AS **MAY** be utilized by multiple IX fabrics operated by the same entity.   
         3. The IXP **SHOULD** use a 16 bit ASN. 
      2. The Route Server **SHALLwill** operate in such a way:	  
         1. That the Route Server AS Number **MUST** not be shown in the AS routing path.  
         2. That the NEXT-HOP **MUST** be the ip address and AS is the originating customer.  
         3. That rather than honoring the NO-EXPORT community, it **MUST** pass that community onto the connected customer.
      3. Route  announcements:  
         1. **MUST** be filtered for reserved or special IP address ranges and AS numbers.  
         2. **MUST** limit the number of BGP prefixes each customer may originate.  
         3. **MUST** disallow the propagation of a default route.  
         4. **RPKI** validation by Route Servers  
            1. **MUST** do RPKI Validation and Drop RPKI Invalids.  
            2. **MUST** update from ALL RIR Trust anchors and delegations  
            3. **MUST** drop all “Stale” records, manifests and CRLs if the time given in their next-update field is in the past.  
            4. Each Route Server **SHOULD** use two different validators.  
         5. **SHOULD** be filtered against the originating networks IRR entries.  
         6. **SHOULD** be filtered against invalid RPKI origination.  
         7. **SHOULD** honor the request of networks not to have announcements in the route servers that the originating networks do not intend to have on route servers (e.g. PeeringDB’s “Never-via-Route-Server”).  
         8. **SHOULD** ensure that paths with well known transit networks are not propagated.  
         9. **SHOULD** limit the use of excessive AS path length.  
         10. **SHOULD** disallow routes that are:   
             1. Shorter than /8 for IPv4 and /19 for IPv6.  
             2. Longer than /24 for IPv4 and /48 for IPv6. except for /32 or /128 for Black Holing purposes.  
         11. The IXP **SHOULD** have at least two route servers. The route servers **SHOULD** be in diverse locations, and connected to discrete switching elements. If the IXP does not have route servers in diverse locations, or does not have two route servers connected to discrete switching elements, it **MUST** be described on the IXP’s publicly available website.  
         12. The IXP **SHOULD** have redundant power feeds fed from discrete sources (A and B) for the Route Servers. If the Route Servers do not have redundant power feeds, it MUST describe where not on a publicly available website.  
         13. The IXP **SHOULD**  publish the Route Server setup on a publically website. If not then the Route Server setup **MUST** be made available to the customer.  
         14. Route Servers filtering policies **MUST** be disclosed to its customer.  
         15. A looking glass **SHOULD** be made available to the customer to verify announcements

   4. ### **Topology**

      If the IXP operates at more than one location, the IXP **MUST** indicate what paths are redundant and **SHOULD** indicate capacity of the links.

## 

4. ## **Operations**

   1. ### NOC

      1. The IXP **MUST** publish a telephone number, email address or any other means that provides immediate access to technical support, on a website available to its customer, on how to contact operational staff that is capable of managing the IXP infrastructure. The access method **MUST** be available 24x7, note this does not mean staff needs to be available 24x7, but the IXP **MUST** publish staff hours.  
      2. The IXP **MUST** provide and publish a procedure to announce service affecting maintenance to its customer.

   2. ### Monitoring {#monitoring}

      1. The IXP **MUST** monitor the exchange platform for performance degradation and service affecting events.  
      2. The IXP **MUST** provide a procedure to inform its customer on performance degradation and service affecting events.

   3. ### Statistics {#statistics}

      1. The IXP **MUST** publish on a publicly available website the customer on the peering platform and the relevant AS numbers.  
      2. The IXP **MUST** publish on a publicly available website the total sum of all incoming and outgoing traffic in bps from all connected networks on the public peering VLAN. The traffic sum **MUST** include the traffic on customer facing ports only and **MUST** be made up of at least 5 min average traffic measurements. A distinction **MUST** be made between the traffic on the public peering VLAN and any other interconnection service.

   4. ### Website {#website}

      The IXP **MUST** have available and maintain a publicly available website where at least the subjects mentioned in this document **MUST** be addressed.

   5. ### Pricing {#pricing}

      The IXP **MUST** disclose any maximum pricing, terms and conditions (if any) on its website.

   6. ### Miscellaneous {#miscellaneous}

      The IXP **MUST** publish and maintain an accurate entry for a peering contact and configuration directory such as [https://www.peeringdb.com](https://www.peeringdb.com/) or [https://ixpdb.euro-ix.net/](https://ixpdb.euro-ix.net/) or any regional IXP organizations. This entry **MUST** contain a list of all facilities that the IXP maintains a point of presence.
