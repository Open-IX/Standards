# Glossary of Data Center and Networking Nomenclature

*This is currently a work in progress and comments are welcome*

## Table of Contents
- [Glossary of Data Center and Networking Nomenclature](#glossary-of-data-center-and-networking-nomenclature)
  - [Table of Contents](#table-of-contents)
  - [I. Data Center Nomenclature](#i-data-center-nomenclature)
  - [II. Sizing, Metrics, and Density](#ii-sizing-metrics-and-density)
  - [III. Edge and Distributed Infrastructure](#iii-edge-and-distributed-infrastructure)
  - [IV. Connectivity and Interconnection](#iv-connectivity-and-interconnection)
  - [V. Facility Infrastructure and Operations](#v-facility-infrastructure-and-operations)
  - [VI. Construction and Form Factors](#vi-construction-and-form-factors)
  - [VII. Security and Access](#vii-security-and-access)
  - [VIII. Reliability and Standards Nomenclature](#viii-reliability-and-standards-nomenclature)
  - [IX. Internet Exchange Point (IXP) Operating Models](#ix-internet-exchange-point-ixp-operating-models)
  - [Appendix: Summary of Data Center Scale Classifications](#appendix-summary-of-data-center-scale-classifications)

---

## I. Data Center Nomenclature

**AI Factory (AI Data Center)**
A marketing term for a specialized facility purpose-built for the training and
operation of massive artificial intelligence (AI) models, characterized by an
architecture centered on Graphics Processing Units (GPUs). These facilities
exhibit Extreme Density (often 40–100+ kW per rack), necessitating advanced
liquid cooling. Unlike traditional enterprise data centers prioritizing
absolute uptime (2N redundancy), AI Factories may accept reduced electrical
redundancy (e.g., N+1 or N) to maximize raw power capacity and cooling
efficiency, as workloads are generally checkpointed.

**Colocation Data Center (Colo / MTDC)**
Third-party, multi-tenant facilities where the provider constructs and manages
the physical infrastructure (power, cooling, security), and tenants lease space
(racks, cages, suites) for their hardware. Enables organizations to outsource
data center requirements, shifting from CAPEX to OPEX while gaining
enterprise-grade infrastructure. Often utilized as a hub for interconnection and
hybrid cloud architectures.

**Carrier Hotel (Telco Hotel)**
A specialized colocation data center typically in central urban locations,
focused on telecommunications carriers and network connectivity. Their primary
function is facilitating traffic exchange (Peering) via extensive fiber
interconnections and Meet-Me-Rooms (MMRs). The core value proposition is Network
Density. Often older legacy buildings with lower power density but massive
ecosystem gravity.

**Cryptocurrency Mines**
Industrial facilities engineered around the arbitrage between energy costs and
the market value of mined coins. Operating under a "Minimal Viable
Infrastructure" philosophy, they deliberately exclude redundancy (UPS,
generators) because operational downtime is an acceptable business risk. Common
cooling methods include Open-Air or evaporative cooling.

**Data Center Provider**
The entity providing space, power, cooling, security, and related services to
customers, including the IXP.

**Enterprise Data Center**
A private facility owned, operated, and exclusively utilized by a single
organization. Emphasizes risk mitigation, control, and customization to meet
specific operational or compliance mandates. Capacities range from hundreds of
kilowatts up to 20 MW; essential for regulated industries requiring Data
Sovereignty.

**Hyperscale Data Center**
Massive facilities designed and operated by technology conglomerates (AWS,
Google, Microsoft, Meta) to support cloud services and vast compute/storage
scalability. Defined by extreme scale (>5,000 servers, 100,000+ sq ft, 20 MW to
650+ MW). They prioritize extreme operational efficiency (PUE often ≤1.1) and
utilize custom hardware (White-Box Servers).

**Managed Services Data Center**
Facilities where a Managed Service Provider (MSP) offers comprehensive
management solutions (server, storage, network administration, 24/7 monitoring),
enabling complete infrastructure outsourcing.

**Retail Colocation**
Colocation tailored to customers requiring smaller footprints. Space is
typically leased by the rack, cage, or Rack Unit (U), generally fewer than 10
racks or <100kW. Frequently incorporates "Remote Hands" support.

**Wholesale Colocation**
Leasing large blocks of power and dedicated space (entire halls or floors) to a
single tenant. Pricing is based on Megawatts (MW) and square footage, usually
metered. Typical leases are 5–15 years for 1–5 MW increments.

**Supercomputing Centers (HPC)**
Government, academic, or research facilities designed for high-end scientific
modeling and simulation. Performance is measured in Flops (Floating Point
Operations per Second), utilizing highly customized computational hardware.

**Mega Data Center**
The largest classification based on rack count, accommodating 9,000+ racks with
power demands typically exceeding 100MW, serving massive cloud operations.

**Multi-Tenant Data Center (MTDC)**
A large infrastructure facility shared by multiple distinct organizations where
logical and physical separation of resources is meticulously maintained.

**Data Center Campus**
A regionally local cluster of Data Centers operated by a single entity, allowing
for seamless interconnection between tenants across different facilities.

## II. Sizing, Metrics, and Density

**Critical IT Load**
The definitive unit of measurement adopted by the industry for data center
sizing, supplanting square footage.

**Kilowatt (kW)**
The standard unit for measuring Power Density or power consumption of individual
racks. Utilized for sizing smaller facilities (Micro/Enterprise).

**Megawatt (MW)**
The standard unit for quantifying the aggregate capacity of Wholesale,
Colocation, and Hyperscale facilities. Refers to the conditioned power a
facility can continuously supply to the IT floor.

**Raised Floor Space**
The historical primary metric for measuring data centers (sq ft or sq m). Due to
increasing rack density, it is now considered a secondary or misleading metric
for technical sizing.

**Power Density**
The power draw per rack, expressed in kW/rack, which determines the required
cooling architecture.

* **Low Density**: <5 kW/rack (Legacy enterprise).

* **Standard / Medium Density**: 5–10 kW/rack (Modern retail colo / general cloud).

* **High Density**: 10–30 kW/rack (Intensive virtualization / storage arrays).

* **Ultra-High / Extreme Density / AI-Ready**: >30 kW/rack. Air cooling becomes
  infeasible, necessitating liquid cooling.

**Liquid Cooling**
A thermal management technique that replaces or augments air cooling by using
fluids (water, dielectric fluids) to remove heat from IT components. Essential
for Ultra-High Density racks (AI/HPC) exceeding 30 kW, where air cooling is
physically insufficient. Approaches include Direct-to-Chip (DtC) and Immersion
Cooling.

**Power Usage Effectiveness (PUE)**
A metric assessing energy efficiency (Total Facility Power / IT Equipment
Power). A PUE of 1.1 or lower signifies exceptionally high efficiency.

**Flops**
Floating Point Operations per Second; the performance metric used in
Supercomputing.

**Petascale Data Center**
Facilities capable of 10^15 operations per second.

**Exascale Data Center**
Facilities achieving 10^18 operations per second.

## III. Edge and Distributed Infrastructure

**Edge Computing**
A computational topology emphasizing the physical placement of compute and
storage resources in close proximity to the user or data generation point to
mitigate latency, optimize bandwidth, and enhance reliability.

**Edge Data Center**
Decentralized physical facilities strategically situated near end-users or
primary data sources. Essential for ultra-low latency applications (5G, IoT,
autonomous vehicles). IT load capacity typically ranges from 50 kW to 500 kW.

* **Extra Small**: Extra Small Edge Facility - Street Furniture or Pole/Wall
  Mounted System.

* **Small**: Small Edge Facility. Entry Level. Small Cabinet System or Street
  Furniture 0-4 Racks.

* **Medium**: Medium Edge Facility. 4-14 Racks. Basic Redundancy, Low to
  Moderate Density.

* **Large**: Large Edge Facility. 8-24 Cabinets/Racks. Moderate Redundancy or
  High Density.

* **Extra Large**: XL Edge Facility. 24+ Cabinets/Racks. High Density. High
  Redundancy.

**Regional Edge / Metro Edge**
Installations in "Tier 2" metropolitan areas or suburban peripheries of major
hubs. Function as localized distribution/caching points. Scale generally ranges
from 100 kW to 10 MW.

**Micro Data Center (µDC)**
Highly compact, self-contained environments integrating all infrastructure
(power, cooling, fire suppression) within a condensed footprint (often a single
enclosure). Capacity spans 50 kW to 150 kW (1 to 10 racks).

**Nano Data Center**
The extreme atomization of infrastructure. Direct integration of computing power
into Consumer Premises Equipment (CPE). Often a single rack (24U-42U) drawing
<3.5-7kW, or smaller integrated devices.

**Network Edge / Far Edge / Tower Edge**
Infrastructure located at the physical boundary of a telecom operator's network
(cell towers, utility cabinets) for sub-5ms latency processing.

## IV. Connectivity and Interconnection

**Internet Exchange (IX)**
An IX is the entity that operates one or more switching fabrics at one or more
locations for the purpose of peering (interconnection).

**Internet Exchange Point (IXP)**
A network facility that enables the interconnection of more than two independent
Autonomous Systems, primarily for the purpose of facilitating the exchange of
Internet traffic. An IXP provides interconnection only for Autonomous Systems.
An IXP does not require the Internet traffic passing between any pair of
participating Autonomous Systems to pass through any third Autonomous System,
nor does it alter or otherwise interfere with such traffic. Note that
“Autonomous Systems” has the meaning given in BCP6/RFC4271.

**Cable Landing Station (CLS)**
Coastal facilities where submarine cables terminate and connect with terrestrial
networks. Often integrated with data centers.

**Carrier Neutral**
A facility (or MMR) permitting any carrier to provide services, preventing
operator monopolies on bandwidth and lowering costs for tenants.

**Meet-Me-Room (MMR)**
The central physical nexus of a highly connected facility. A secure, managed
area where fiber optic cables from various tenants and carriers are
cross-connected. Should ideally contain little to no powered equipment.

**MMR Operator**
The entity that controls and operates one or multiple designated
Meet-Me-Rooms (MMRs) in the building. The MMR operator provides the
infrastructure and management to support interconnection of network providers
with each other and cross-connection either from network provider to building
tenant or amongst building tenants. The MMR may include a variety of media
types, including but not limited to: single and multi-mode fiber as well as
Cat 5 copper or similar legacy infrastructure.

**Cross Connect**
A physical patch cable (usually fiber) installed to connect one tenant's
equipment to another's (or to a carrier). Can be routed via an MMR or run
direct (Home Run) from rack to rack.

**Virtual Cross-Connect**
A software-defined interconnection that logically functions like a physical
cross-connect. Often provisioned instantly over a shared network fabric or
Software-Defined Network (SDN) platform.

**Data Gravity**
The phenomenon where a large aggregation of data attracts additional
applications and services to co-locate nearby to minimize latency and transfer
costs.

**Interconnection Hub**
A modern designation for a highly connected facility accommodating carriers,
Cloud On-Ramps, CDNs, and IXPs.

**Peering (Paid vs. Settlement-Free)**
The reciprocal exchange of traffic between distinct networks.

* **Settlement-Free Peering**: Networks exchange traffic without exchanging
  money, assuming mutual benefit.

* **Paid Peering**: One network pays the other for access to their network
  routing table, often bordering on transit agreements.

**Cloud Onramp**
A dedicated, private physical or virtual connection directly into a public cloud
provider's edge node (e.g., AWS Direct Connect, Azure ExpressRoute). It bypasses
the public internet for better security and predictable latency.

**Backhaul**
The portion of a hierarchical telecommunications network linking the core
network (backbone) to the edge subnetworks.

**Last-Mile**
The final leg of the telecommunications network delivering connectivity directly
to the retail end-user or enterprise premise.

**Metro Interconnect**
High-capacity network fiber connections spanning a metropolitan area, linking
distinct data centers, carrier hotels, and enterprise offices.

**Data Center Interconnect (DCI)**
Networking solutions utilizing high-speed packet-optical connectivity to link
two or more data centers over short, medium, or long distances.

**Layer 2 vs. Layer 3 Interconnect**

* **Layer 2 Interconnect**: Connects networks at the Data Link layer (MAC
  addresses, VLANs). Used heavily in IXPs to allow peering across a shared
  broadcast domain.

* **Layer 3 Interconnect**: Connects networks at the Network layer via routing
  protocols (IP addresses, BGP, OSPF).

**VxLAN (Virtual Extensible LAN)**
A network virtualization technology that encapsulates MAC-based Layer 2 frames
within Layer 4 UDP packets. Crucial for massive cloud computing, allowing
Layer 2 overlay networks to scale across Layer 3 boundaries.

**MPLS (Multiprotocol Label Switching)**
A routing technique that directs data from one node to the next based on short
path labels rather than complex network addresses, speeding up traffic flow and
allowing for traffic engineering.

**Edge Router**
A specialized, high-capacity router situated at the boundary of a network,
handling traffic leaving or entering the autonomous system.

**Facilities-based Network Provider**
The entity that controls and maintains a physical fiber path into a building.
Multiple providers may lease or share this fiber.

**LACP / LAG (Physical Interface Speeds)**
Link Aggregation Group (LAG) combines multiple physical network ports into a
single logical port to increase bandwidth and provide redundancy. Link
Aggregation Control Protocol (LACP) is the standard protocol that negotiates and
manages this bundling.

**Fiber Distribution Panel (FDP) / Optical Distribution Frame (ODF)**
High-density, passive physical infrastructure where external or campus fiber
cables are spliced, organized, and cross-connected to internal equipment.

**Optical Splitter**
A passive component that takes a single beam of light and divides it into
multiple outbound beams (e.g., a 1:32 or 1:64 split). It is the core enabler of
all Passive Optical Network (PON) architectures.

**GPON (Gigabit Passive Optical Network)**
A point-to-multipoint access standard utilizing passive splitters to provide
high bandwidth (typically 2.5 Gbps downstream, 1.25 Gbps upstream) over a single
fiber strand.

**OLT (Optical Line Terminal)**
The provider-side aggregation equipment of a GPON network. It sits in the data
center or central office, controls bandwidth allocation, and manages downstream
endpoints.

**ONT / ONU (Optical Network Terminal / Unit)**
The end-user boundary device that converts optical signals back into usable
electrical signals (Ethernet, Wi-Fi). ONT and ONU refer to essentially the same
hardware at the customer premise, depending on the specific standard body
referenced.

**ODN (Optical Distribution Network)**
The entirely passive physical fiber infrastructure (the cables, splitters, and
FDPs) residing between the OLT and the ONT/ONU.

**Wavelength Division Multiplexing (WDM/DWDM)**
Optical multiplexing technology that multiplexes multiple optical carrier
signals onto a single optical fiber by using different wavelengths (colors) of
laser light, vastly increasing total network capacity.

**Optical Transceivers (SFP, QSFP, OSFP)**
Hot-pluggable optic modules that interface with edge routers and switches,
converting electrical data signals into light for transmission over fiber optic
cables.

**IXP Member, Participant, and Customer Terminology**

* **Participant**: Broadly, any entity physically and logically connected to an
  IXP switching fabric.

* **Member**: An entity that participates in an IXP, often implying governance,
  voting rights, or cooperative ownership (especially in non-profit/community
  IXPs).

* **Customer**: An entity paying for access to an IXP, a term usually favored by
  For-Profit IXP operators.

* **Member Network**: The actual Autonomous System (AS) and physical routing
  equipment terminating the connection.

* **IX End User**: The consumer or enterprise downstream from the peering
  networks, whose traffic is improved by the IXP.

## V. Facility Infrastructure and Operations

**Medium Voltage (MV) Switchgear**
Heavy-duty electrical equipment used to control, protect, and isolate power
systems. Bridging utility transmission and site distribution, medium voltage in
data centers generally falls between 15kV and 38kV.

**Automatic Transfer Switch (ATS)**
A critical mechanism that automatically transfers the facility's electrical load
from the primary utility feed to the backup generators in the event of a power
anomaly or outage.

**Uninterruptible Power Supply (UPS)**
A critical electrical apparatus that provides instantaneous emergency power to a
load when the primary input power source fails, typically using batteries or
flywheels. It bridges the gap until standby diesel generators can start and
synchronize.

**Power Distribution Unit (PDU)**

* **Floor PDU / Remote Power Panel (RPP)**: Standalone cabinets downstream from
  the UPS that step down facility voltage to usable rack voltage and distribute
  it via circuit breakers to the data hall rows.

* **Rack PDU (rPDU)**: The power strip mounted directly inside the IT cabinet,
  ranging from basic distribution to fully metered, remotely switched models.

**CRAC / CRAH**

* **CRAC (Computer Room Air Conditioner)**: Uses a built-in compressor and
  chemical refrigerants to cool the air.

* **CRAH (Computer Room Air Handler)**: Uses fans and cooling coils through
  which chilled water (supplied by a central plant) circulates to remove heat.

**Hot Aisle / Cold Aisle**
A fundamental data center layout design. Server racks are aligned in alternating
rows so that cold air intake faces one way (Cold Aisle) and hot air exhaust
faces the other (Hot Aisle). This prevents the mixing of hot and cold air,
drastically improving cooling efficiency.

**Central Utility Plant (CUP)**
A centralized facility separated from the IT data halls that houses the
primary, heavy infrastructure for producing chilled water (chillers, cooling
towers) and sometimes primary electrical switchgear.

**NOC (Network Operations Center)**
A centralized location where engineers continuously monitor, manage, and
maintain the health and performance of the network infrastructure and switching
fabrics.

**FOC (Facility Operations Center)**
The command center dedicated to monitoring and managing the physical
infrastructure of the data center, including power distribution, cooling,
environmental sensors, and physical security.

**SOC (Security Operations Center)**
A centralized unit that monitors an organization's IT infrastructure for
cybersecurity threats, defending against intrusions and managing incident
response.

## VI. Construction and Form Factors

**Base Building**
Shall designate the fee simple ownership and/or control of the underlying real
estate. This entity ultimately controls the right of network entry, but may
grant broad and open rights of access to the MMR Operator or Data Center
Provider as defined below.

**Brownfield Data Center**
Existing structures retrofitted for data center use. Facilitates expedited
deployment but may encounter infrastructure limitations.

**Greenfield Data Center**
Entirely new facilities constructed on undeveloped land, designed to precise
specifications without pre-existing constraints.

**Containerized Data Center**
Infrastructure integrated within standard ISO shipping containers (20ft or
40ft). Highly mobile, suitable for disaster recovery or remote capacity
(typically 13–26 racks).

**Mobile Data Center**
Fully portable centers mounted on trucks or trailers, enabling rapid deployment
within hours.

**Modular Data Center (MDC)**
Systems assembled using pre-engineered, prefabricated modules assembled and
tested in a factory. Reduces deployment timelines significantly.

**Prefabricated / Skid-Mounted Data Center**
Critical components (Power/Cooling skids) pre-assembled on structural steel
frames in a factory, engineered for swift installation within a shell building.

**Powered Shell Data Center**
Partially completed facilities where the developer finalizes the building
exterior and core utilities, allowing tenants to customize the interior
build-out.

**Underground / Floating Data Centers**

* **Underground**: Built in mines/bunkers; provides physical hardening and
  natural thermal regulation.

* **Floating (Data Barges)**: Situated on vessels leveraging surrounding water
  for highly efficient heat rejection.

## VII. Security and Access

**Mantrap (Security Portal)**
A physical security access control system consisting of a small space with two
sets of interlocking doors. The first door must close and lock before the
second door can be opened, preventing tailgating and ensuring proper
biometric/badge authentication.

**Anti-Tailgating / Anti-Passback**

* **Anti-tailgating**: Sensor or turnstile systems designed to prevent an
  unauthorized individual from following an authorized person through a secure
  doorway.

* **Anti-passback**: System programming that prevents a credential holder from
  passing their badge backward through a door for another person to use.

**Biometric Access Control**
The use of unique physical characteristics—such as fingerprint, iris, or facial
recognition—to verify identity. This ensures physical presence rather than mere
possession of a keycard.

**Multi-Factor Authentication (MFA)**
Requiring two or more independent forms of verification to grant physical
access, typically combining something a person has (RFID badge), something they
know (PIN), and something they are (biometrics).

**Defense-in-Depth (Physical)**
A layered security architecture creating multiple, concentric rings of
protection (e.g., perimeter fencing -> lobby turnstiles -> data hall mantrap ->
locked server cabinet). A breach of one layer does not compromise the entire
facility.

**Bollards (Crash-Rated)**
Heavy-duty steel or concrete perimeter barriers specifically engineered to
protect the facility's exterior walls, entryways, and external generators from
vehicle-ramming attacks.

**Role-Based Access Control (RBAC)**
In a physical security context, this involves restricting an employee or
vendor's badge access strictly to the specific data halls, cages, or zones
required for their job function, rather than granting blanket facility access.

## VIII. Reliability and Standards Nomenclature

**Uptime Institute Tiers**
The international standard for classifying data center availability:

* **Tier I (Basic Capacity)**: Single path, no redundancy (N). 99.671%
  availability.

* **Tier II (Redundant Capacity)**: Single path, redundant components (N+1).
  99.741% availability.

* **Tier III (Concurrently Maintainable)**: Multiple paths, N+1 redundancy. Any
  component can be removed without shutdown. 99.982% availability.

* **Tier IV (Fault Tolerant)**: Fully redundant (2N or 2N+1), multiple active
  paths. Withstands a single fault without impacting IT load. 99.995%
  availability.

**TIA-942 Ratings**
A standard by the Telecommunications Industry Association ("Rated-1" through
"Rated-4"). Broader scope than Uptime, covering cabling, architecture, and
physical security.

**BICSI Availability Classes**
Standard ranging from Classes 0 through 4. Classes 0 and 1 address facilities
where downtime is acceptable (e.g., crypto mining).

**Availability Zone (AZ)**
Logical groupings of proximate data centers within a Cloud Region. Each AZ
operates with independent power/cooling/networking to ensure fault tolerance
but is treated logically as a single failure domain by cloud platforms.

## IX. Internet Exchange Point (IXP) Operating Models

(Note: Definitions sourced from "Community-Driven IXPs: Enhancing Local
Connectivity and Sustainability" by Internet Society, CC BY-NC-SA 4.0)

**Member-Operated IXP (Community-driven)**
Governance is led by members through an elected board. Non-profit, democratic
organizations created to enhance connectivity for their members.

**ISP Association-Operated IXP**
Established by a consortium of major ISPs who collaborate on bylaws. Staffing
is typically funded by the consortium to optimize regional interconnectivity.

**For-Profit IXP**
A commercial venture managed by private entities generating revenue by offering
a neutral peering environment and a broad range of services.

**Academia/Regulator-Managed IXP**
Management overseen by an academic institution or regulator. Supports research
and education goals while functioning as a neutral peering point.

**Informally Managed IXP**
Lacks formal structure; relies on mutual cooperation of benefiting networks.
Long-term viability is often debated.

**ISP-Operated IXP**
Run by a single ISP. Can create neutrality concerns; may require regulatory
oversight to ensure fair access.

## Appendix: Summary of Data Center Scale Classifications

| Classification | Typical Physical Footprint | Typical Power Capacity | Key Application |
| --- | --- | --- | --- |
| Nano | 1–50 sq ft (1 Rack/Enclosure) | < 7 kW | IoT Gateways, CPE integration, Fog computing |
| Micro (µDC) | 1–500 sq ft (1–10 Racks) | < 100 kW – 150 kW | Cell Tower installations, Smart Buildings |
| Mini | Up to 10 racks | Basic capacity | Supporting startups/small businesses |
| Small / Server Room | 1,000–5,000 sq ft | 100 kW – 500 kW | SMB on-premises servers |
| Medium / Enterprise | 5,000–20,000 sq ft | 1 MW – 5 MW | Corporate HQ, Private Cloud, Regional Hubs |
| Regional Edge | 50,000–100,000 sq ft | 2 MW – 10 MW | Localized content delivery caching |
| Large / Wholesale | 20,000–100,000 sq ft | 5 MW – 20 MW | Multi-tenant Colo, Enterprise Hubs |
| Massive / Hyperscale | 100,000+ sq ft | > 20 MW (up to 650+ MW) | Cloud Service Providers, Major Social Media |
| Mega Campus | 1M+ sq ft (multi-building) | > 100 MW (up to 240+ MW) | Largest cloud service operations |
