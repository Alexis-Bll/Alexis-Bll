

network-lab-portfolio-main (5).zip
Zip Archive
where did we get up to from last time?


Worked for 49s
Based on the latest repository ZIP, we had reached the end of V2 Lab 03.

Completed
Root portfolio README.md

Main enterprise-network-lab/README.md

V1 and V2 topology documentation, including the Draw.io diagrams and EVE-NG screenshots

01 – Internet Edge & NAT

02 – DHCP Services

03 – DNS & Domain Services

DNS

Active Directory

Domain joins across VLANs

OUs, users and security groups

Shared-folder permissions

Group Policy testing

Next file
The next write-up is:

enterprise-network-lab/labs/v2/04-application-server-integration.md
It currently only contains:

Work In Progress!
After that, the final V2 lab document will be:

05-testing-validation.md
One issue I noticed
The following file appears to have been accidentally filled with another version of the Internet Edge documentation:

enterprise-network-lab/labs/v2/README.md
That file should instead be the V2 labs overview/index, linking to Labs 01–05 and showing their completion status.

So our best order is:

Correct the V2 README.md

Create 04 – Application Server Integration

Create 05 – Testing & Validation

Review the V2 configuration-change files and perform a final consistency check

The next main implementation document we were about to work on was 04 – Application Server Integration. I also still have the supplied GitHub repository reference. 



Can you give me the raw markdown file to replace the v2 readme that is missing.

Worked for 54s
Replace the contents of:

enterprise-network-lab/labs/v2/README.md
with the following:

Enterprise Network Lab - V2
Overview
V2 is the enterprise services expansion of the completed Enterprise Network Lab V1.

V1 established the core networking foundation, including VLANs, inter-VLAN routing, OSPF, HSRP, EtherChannel, ACLs, and Layer 2 security. V2 builds on that working network by introducing internet edge connectivity and centralised infrastructure services commonly found in business environments.

V2 introduces:

Internet edge connectivity

NAT/PAT for outbound traffic

Default route advertisement through OSPF

Centralised DHCP services

DHCP relay across routed networks

DNS services

Active Directory Domain Services

Domain-joined clients

Organisational Units, users, and security groups

Group Policy

Shared-resource permissions

Application server integration

Final service and connectivity validation

V2 is the final planned expansion of this lab.

V2 Status
Status: In Progress

The core V2 infrastructure services have been implemented and documented.

Completed areas include:

Internet edge connectivity

NAT/PAT

Default route advertisement

Centralised DHCP

DHCP relay

DNS

Active Directory

Domain joins

User and group management

Shared-folder permissions

Group Policy testing

Remaining areas include:

Application server integration

Final end-to-end testing

Final configuration-change documentation

Lab Objectives
The objectives of V2 are to:

Extend the completed V1 network without redesigning the original topology

Provide simulated internet access through a centralised HQ edge

Translate private internal addresses using NAT/PAT

Advertise a default route through OSPF

Replace static client addressing with centralised DHCP

Relay DHCP traffic between VLANs and remote branch networks

Deploy internal DNS and Active Directory services

Join clients from multiple VLANs to a central domain

Organise users and computers using Active Directory OUs

Implement group-based access control

Apply and validate Group Policy settings

Integrate an internal application server

Test connectivity, authentication, name resolution, permissions, and service availability

Document troubleshooting and design decisions clearly

Relationship to V1
V2 does not replace the completed V1 network.

It adds enterprise services to the existing routing, switching, redundancy, segmentation, and security design.

Area	V1	V2
HQ and branch topology	Implemented	Retained
VLAN segmentation	Implemented	Retained
Inter-VLAN routing	Implemented	Retained
OSPF routing	Implemented	Extended with default route advertisement
HSRP redundancy	Implemented	Retained
STP and EtherChannel	Implemented	Retained
ACL segmentation	Implemented	Retained and reviewed where required
Layer 2 security	Implemented	Adjusted to support DHCP services
Client addressing	Static	Centralised DHCP
Internet access	Not included	Added through HQ-R1
NAT/PAT	Not included	Added
DNS	Not included	Added
Active Directory	Not included	Added
Group Policy	Not included	Added
Application services	Not included	Added
This demonstrates how an established network can be expanded incrementally while preserving its original design.

Topology Summary
V2 retains the multi-site enterprise topology from V1 and introduces additional infrastructure services.

The environment contains:

A headquarters site

Two branch sites

A private WAN/MPLS-style provider network

Redundant HQ core switches

HQ access and server switches

Engineering and Sales branch networks

A simulated internet connection

A Windows Server domain controller

An internal application server

Domain-joined client devices

The complete V2 topology is documented here:

V2 Topology Documentation

V2 Logical Network Diagram

V2 EVE-NG Topology

Architecture Summary
Area	Devices / Services	Purpose
HQ Core	HQ-CSW1 and HQ-CSW2	Inter-VLAN routing, HSRP, OSPF, STP control, and EtherChannel
HQ Access	HQ-ASW1 and HQ-ASW2	Admin client connectivity
HQ Server Access	HQ-SSW1 and HQ-SSW2	Server VLAN connectivity
HQ Edge	HQ-R1 and HQ-R2	WAN routing and redundant HQ connectivity
Internet Edge	HQ-R1	NAT/PAT and simulated internet access
Private WAN	ISP router	Routed connectivity between HQ and both branches
Branch 1	BR1 and BR-SW1	Engineering branch connectivity
Branch 2	BR2 and BR-SW2	Sales branch connectivity
Domain Services	DC1	DHCP, DNS, Active Directory, and Group Policy
Application Services	Application Server	Internal application and service-access testing
VLAN and IP Addressing Summary
VLAN	Name / Purpose	Subnet	Default Gateway
VLAN 10	Admin	192.168.10.0/24	192.168.10.1 through HSRP
VLAN 20	Servers	192.168.20.0/24	192.168.20.1 through HSRP
VLAN 30	Engineering Branch	192.168.30.0/24	192.168.30.1 through BR1
VLAN 40	Sales Branch	192.168.40.0/24	192.168.40.1 through BR2
The WAN and routed transit links continue to use private 10.0.0.0/8 addressing with /30 point-to-point subnets.

Infrastructure Services
Device	IP Address	VLAN	Role
DC1	192.168.20.10	VLAN 20	DHCP, DNS, Active Directory, and Group Policy
Application Server	Documented during Phase 04	VLAN 20	Internal application services
Simulated Internet Network
V2 uses a documentation-range subnet to simulate an internet-facing connection:

203.0.113.0/30
HQ-R1 acts as the boundary between the private enterprise network and this simulated external network.

Technologies Implemented
V2 demonstrates the following technologies and services:

Internet edge design

Static default routing

OSPF default route advertisement

Network Address Translation

Port Address Translation

NAT inside and outside interface roles

Centralised Windows DHCP

DHCP scopes and options

DHCP relay using ip helper-address

DHCP Snooping integration

Dynamic ARP Inspection considerations

DNS name resolution

Active Directory Domain Services

Active Directory-integrated DNS

Domain joins across routed VLANs

Organisational Units

Domain users and security groups

Role-Based Access Control

NTFS and share permissions

Group Policy Objects

Internal application server integration

Cross-VLAN service validation

Troubleshooting and verification

Documentation Structure
The V2 documentation is divided into five implementation phases.

Phase	Status	Document	Description
01	Completed	Internet Edge and NAT	Internet-facing connectivity, PAT, default routing, and OSPF default route advertisement
02	Completed	DHCP Services	Windows DHCP, client scopes, DHCP relay, DHCP Snooping, and troubleshooting
03	Completed	DNS and Domain Services	DNS, Active Directory, domain joins, users, groups, permissions, and Group Policy
04	In Progress	Application Server Integration	Internal application server deployment, access requirements, and service testing
05	In Progress	Testing and Validation	Final connectivity, service, authentication, policy, NAT, and failover validation
Recommended Reading Order
Review the V2 documentation in the following order:

Internet Edge and NAT

DHCP Services

DNS and Domain Services

Application Server Integration

Testing and Validation

This follows the order in which external connectivity and internal infrastructure services were introduced into the existing network.

Key Design Decisions
Incremental Expansion
V2 keeps the working V1 architecture rather than replacing it.

The existing VLANs, routing, redundancy, ACLs, and Layer 2 security controls remain in place. New services are added only where required.

This reflects how production networks are commonly expanded over time.

Centralised Internet Breakout
HQ-R1 acts as the central internet edge router.

Internal devices and branch networks send external traffic towards HQ-R1 using a default route advertised through OSPF.

HQ-R1 then performs NAT/PAT before forwarding the traffic to the simulated external network.

Centralised Infrastructure Services
DC1 is placed in the HQ server VLAN and provides services to clients across the enterprise network.

DC1 provides:

DHCP

DNS

Active Directory Domain Services

Authentication

Group Policy

Centralising these services makes administration more consistent and allows remote branch clients to use the same infrastructure as HQ clients.

DHCP Relay
DHCP broadcasts do not cross routed boundaries by default.

The ip helper-address command is therefore configured on the appropriate Layer 3 gateway interfaces to forward DHCP requests to DC1.

This allows clients in the Admin, Engineering, and Sales networks to obtain addressing from one central server.

DNS and Active Directory Dependency
Domain clients use DC1 as their primary DNS server.

This is required because Active Directory relies on DNS records to locate domain controllers and domain services.

Using external DNS directly on domain clients could prevent domain joins, authentication, and Group Policy processing from working correctly.

Layer 2 Security Integration
The DHCP services introduced in V2 had to work alongside the DHCP Snooping and Dynamic ARP Inspection controls configured in V1.

This required the trust boundary and binding behaviour to be reviewed so that legitimate DHCP traffic was not blocked.

This demonstrates that security controls must be reconsidered when infrastructure services change.

Application Server Placement
The application server is placed in the dedicated server VLAN.

This separates server workloads from user devices and allows access to the application to be tested from multiple departments and branch networks.

Service Flow
A typical client startup and authentication process follows this sequence:

Client starts
    ↓
DHCP request is relayed to DC1
    ↓
Client receives IP address, gateway, and DNS settings
    ↓
Client queries DC1 for internal DNS records
    ↓
Client locates the lab.local domain
    ↓
User authenticates against Active Directory
    ↓
Group Policy and permissions are applied
    ↓
Client accesses authorised internal services
For external connectivity:

Internal client
    ↓
Local default gateway
    ↓
OSPF-learned default route
    ↓
HQ-R1
    ↓
NAT/PAT translation
    ↓
Simulated external network
Current Implementation Status
Completed
Simulated internet connection

HQ-R1 internet edge configuration

NAT/PAT configuration

Default route configuration

OSPF default route advertisement

Windows DHCP deployment

DHCP scopes and options

DHCP relay

DHCP lease validation

DNS deployment

Active Directory domain deployment

Domain joins across multiple VLANs

OU structure

User and security-group creation

Shared-folder permissions

Group Policy testing

Remaining
Application server deployment and integration documentation

Application access and permission testing

Final end-to-end service validation

Final V2 configuration-change review

Final documentation consistency check

Skills Demonstrated
V2 is intended to demonstrate practical skills relevant to junior networking and infrastructure roles.

These include:

Expanding an existing network design

Configuring enterprise edge routing

Implementing and verifying NAT/PAT

Advertising a default route through OSPF

Deploying centralised DHCP

Configuring DHCP relay across VLANs and WAN links

Integrating Windows Server services with network infrastructure

Troubleshooting DNS and domain-join issues

Managing Active Directory users, groups, and OUs

Applying Group Policy

Implementing group-based resource access

Testing services across routed network boundaries

Documenting technical implementation and troubleshooting clearly

V2 Scope
Included in V2
Simulated internet connectivity

Centralised internet breakout

NAT/PAT

OSPF default route advertisement

Centralised DHCP

DHCP relay

DNS

Active Directory

Domain-joined endpoints

Organisational Units

Users and security groups

Group Policy

Shared-resource permissions

Application server integration

Final service testing and validation

Outside the Scope of V2
Public cloud integration

Multi-domain Active Directory

Multiple domain controllers

Production internet connectivity

Public DNS hosting

Enterprise firewall appliances

VPN remote access

Wireless infrastructure

High-availability server clustering

These features are outside the intended scope of this portfolio lab.

Related Files
Topology
V2 Topology

Topology Overview

Configurations
Full Device Configurations

V2 Configuration Changes

Other Documentation
V1 Lab Documentation

Lab Documentation Overview

Enterprise Network Lab Overview

Main Portfolio README

Summary
V2 expands the completed CCNA-level network foundation from V1 into a more complete enterprise environment.

It demonstrates how internet access, address translation, centralised IP allocation, DNS, identity services, access control, Group Policy, and internal application services can be integrated into an existing multi-site network.

The completed V2 documentation will show not only the final configuration, but also the design reasoning, validation process, troubleshooting steps, and practical lessons learned during implementation.

This restores the V2 folder as an overview and navigation page rather than duplicating the Internet Edge lab.


Can you convert it to raw markdown file format to copy and paste into github.

Copy everything below into:

enterprise-network-lab/labs/v2/README.md

Enterprise Network Lab - V2
Overview
V2 is the enterprise services expansion of the completed Enterprise Network Lab V1.

V1 established the core networking foundation, including VLANs, inter-VLAN routing, OSPF, HSRP, EtherChannel, ACLs, and Layer 2 security. V2 builds on that working network by introducing internet edge connectivity and centralised infrastructure services commonly found in business environments.

V2 introduces:

Internet edge connectivity

NAT/PAT for outbound traffic

Default route advertisement through OSPF

Centralised DHCP services

DHCP relay across routed networks

DNS services

Active Directory Domain Services

Domain-joined clients

Organisational Units, users, and security groups

Group Policy

Shared-resource permissions

Application server integration

Final service and connectivity validation

V2 is the final planned expansion of this lab.

V2 Status
Status: In Progress

The core V2 infrastructure services have been implemented and documented.

Completed areas include:

Internet edge connectivity

NAT/PAT

Default route advertisement

Centralised DHCP

DHCP relay

DNS

Active Directory

Domain joins

User and group management

Shared-folder permissions

Group Policy testing

Remaining areas include:

Application server integration

Final end-to-end testing

Final configuration-change documentation

Lab Objectives
The objectives of V2 are to:

Extend the completed V1 network without redesigning the original topology

Provide simulated internet access through a centralised HQ edge

Translate private internal addresses using NAT/PAT

Advertise a default route through OSPF

Replace static client addressing with centralised DHCP

Relay DHCP traffic between VLANs and remote branch networks

Deploy internal DNS and Active Directory services

Join clients from multiple VLANs to a central domain

Organise users and computers using Active Directory OUs

Implement group-based access control

Apply and validate Group Policy settings

Integrate an internal application server

Test connectivity, authentication, name resolution, permissions, and service availability

Document troubleshooting and design decisions clearly

Relationship to V1
V2 does not replace the completed V1 network.

It adds enterprise services to the existing routing, switching, redundancy, segmentation, and security design.

Area	V1	V2
HQ and branch topology	Implemented	Retained
VLAN segmentation	Implemented	Retained
Inter-VLAN routing	Implemented	Retained
OSPF routing	Implemented	Extended with default route advertisement
HSRP redundancy	Implemented	Retained
STP and EtherChannel	Implemented	Retained
ACL segmentation	Implemented	Retained and reviewed where required
Layer 2 security	Implemented	Adjusted to support DHCP services
Client addressing	Static	Centralised DHCP
Internet access	Not included	Added through HQ-R1
NAT/PAT	Not included	Added
DNS	Not included	Added
Active Directory	Not included	Added
Group Policy	Not included	Added
Application services	Not included	Added
This demonstrates how an established network can be expanded incrementally while preserving its original design.

Topology Summary
V2 retains the multi-site enterprise topology from V1 and introduces additional infrastructure services.

The environment contains:

A headquarters site

Two branch sites

A private WAN/MPLS-style provider network

Redundant HQ core switches

HQ access and server switches

Engineering and Sales branch networks

A simulated internet connection

A Windows Server domain controller

An internal application server

Domain-joined client devices

The complete V2 topology is documented here:

V2 Topology Documentation

V2 Logical Network Diagram

V2 EVE-NG Topology

Architecture Summary
Area	Devices / Services	Purpose
HQ Core	HQ-CSW1 and HQ-CSW2	Inter-VLAN routing, HSRP, OSPF, STP control, and EtherChannel
HQ Access	HQ-ASW1 and HQ-ASW2	Admin client connectivity
HQ Server Access	HQ-SSW1 and HQ-SSW2	Server VLAN connectivity
HQ Edge	HQ-R1 and HQ-R2	WAN routing and redundant HQ connectivity
Internet Edge	HQ-R1	NAT/PAT and simulated internet access
Private WAN	ISP router	Routed connectivity between HQ and both branches
Branch 1	BR1 and BR-SW1	Engineering branch connectivity
Branch 2	BR2 and BR-SW2	Sales branch connectivity
Domain Services	DC1	DHCP, DNS, Active Directory, and Group Policy
Application Services	Application Server	Internal application and service-access testing
VLAN and IP Addressing Summary
VLAN	Name / Purpose	Subnet	Default Gateway
VLAN 10	Admin	192.168.10.0/24	192.168.10.1 through HSRP
VLAN 20	Servers	192.168.20.0/24	192.168.20.1 through HSRP
VLAN 30	Engineering Branch	192.168.30.0/24	192.168.30.1 through BR1
VLAN 40	Sales Branch	192.168.40.0/24	192.168.40.1 through BR2
The WAN and routed transit links continue to use private 10.0.0.0/8 addressing with /30 point-to-point subnets.

Infrastructure Services
Device	IP Address	VLAN	Role
DC1	192.168.20.10	VLAN 20	DHCP, DNS, Active Directory, and Group Policy
Application Server	Documented during Phase 04	VLAN 20	Internal application services
Simulated Internet Network
V2 uses a documentation-range subnet to simulate an internet-facing connection:

203.0.113.0/30
HQ-R1 acts as the boundary between the private enterprise network and this simulated external network.

Technologies Implemented
V2 demonstrates the following technologies and services:

Internet edge design

Static default routing

OSPF default route advertisement

Network Address Translation

Port Address Translation

NAT inside and outside interface roles

Centralised Windows DHCP

DHCP scopes and options

DHCP relay using ip helper-address

DHCP Snooping integration

Dynamic ARP Inspection considerations

DNS name resolution

Active Directory Domain Services

Active Directory-integrated DNS

Domain joins across routed VLANs

Organisational Units

Domain users and security groups

Role-Based Access Control

NTFS and share permissions

Group Policy Objects

Internal application server integration

Cross-VLAN service validation

Troubleshooting and verification

Documentation Structure
The V2 documentation is divided into five implementation phases.

Phase	Status	Document	Description
01	Completed	Internet Edge and NAT	Internet-facing connectivity, PAT, default routing, and OSPF default route advertisement
02	Completed	DHCP Services	Windows DHCP, client scopes, DHCP relay, DHCP Snooping, and troubleshooting
03	Completed	DNS and Domain Services	DNS, Active Directory, domain joins, users, groups, permissions, and Group Policy
04	In Progress	Application Server Integration	Internal application server deployment, access requirements, and service testing
05	In Progress	Testing and Validation	Final connectivity, service, authentication, policy, NAT, and failover validation
Recommended Reading Order
Review the V2 documentation in the following order:

Internet Edge and NAT

DHCP Services

DNS and Domain Services

Application Server Integration

Testing and Validation

This follows the order in which external connectivity and internal infrastructure services were introduced into the existing network.

Key Design Decisions
Incremental Expansion
V2 keeps the working V1 architecture rather than replacing it.

The existing VLANs, routing, redundancy, ACLs, and Layer 2 security controls remain in place. New services are added only where required.

This reflects how production networks are commonly expanded over time.

Centralised Internet Breakout
HQ-R1 acts as the central internet edge router.

Internal devices and branch networks send external traffic towards HQ-R1 using a default route advertised through OSPF.

HQ-R1 then performs NAT/PAT before forwarding the traffic to the simulated external network.

Centralised Infrastructure Services
DC1 is placed in the HQ server VLAN and provides services to clients across the enterprise network.

DC1 provides:

DHCP

DNS

Active Directory Domain Services

Authentication

Group Policy

Centralising these services makes administration more consistent and allows remote branch clients to use the same infrastructure as HQ clients.

DHCP Relay
DHCP broadcasts do not cross routed boundaries by default.

The ip helper-address command is therefore configured on the appropriate Layer 3 gateway interfaces to forward DHCP requests to DC1.

This allows clients in the Admin, Engineering, and Sales networks to obtain addressing from one central server.

DNS and Active Directory Dependency
Domain clients use DC1 as their primary DNS server.

This is required because Active Directory relies on DNS records to locate domain controllers and domain services.

Using external DNS directly on domain clients could prevent domain joins, authentication, and Group Policy processing from working correctly.

Layer 2 Security Integration
The DHCP services introduced in V2 had to work alongside the DHCP Snooping and Dynamic ARP Inspection controls configured in V1.

This required the trust boundary and binding behaviour to be reviewed so that legitimate DHCP traffic was not blocked.

This demonstrates that security controls must be reconsidered when infrastructure services change.

Application Server Placement
The application server is placed in the dedicated server VLAN.

This separates server workloads from user devices and allows access to the application to be tested from multiple departments and branch networks.

Service Flow
A typical client startup and authentication process follows this sequence:

Client starts
    ↓
DHCP request is relayed to DC1
    ↓
Client receives IP address, gateway, and DNS settings
    ↓
Client queries DC1 for internal DNS records
    ↓
Client locates the lab.local domain
    ↓
User authenticates against Active Directory
    ↓
Group Policy and permissions are applied
    ↓
Client accesses authorised internal services
For external connectivity:

Internal client
    ↓
Local default gateway
    ↓
OSPF-learned default route
    ↓
HQ-R1
    ↓
NAT/PAT translation
    ↓
Simulated external network
Current Implementation Status
Completed
Simulated internet connection

HQ-R1 internet edge configuration

NAT/PAT configuration

Default route configuration

OSPF default route advertisement

Windows DHCP deployment

DHCP scopes and options

DHCP relay

DHCP lease validation

DNS deployment

Active Directory domain deployment

Domain joins across multiple VLANs

OU structure

User and security-group creation

Shared-folder permissions

Group Policy testing

Remaining
Application server deployment and integration documentation

Application access and permission testing

Final end-to-end service validation

Final V2 configuration-change review

Final documentation consistency check

Skills Demonstrated
V2 is intended to demonstrate practical skills relevant to junior networking and infrastructure roles.

These include:

Expanding an existing network design

Configuring enterprise edge routing

Implementing and verifying NAT/PAT

Advertising a default route through OSPF

Deploying centralised DHCP

Configuring DHCP relay across VLANs and WAN links

Integrating Windows Server services with network infrastructure

Troubleshooting DNS and domain-join issues

Managing Active Directory users, groups, and OUs

Applying Group Policy

Implementing group-based resource access

Testing services across routed network boundaries

Documenting technical implementation and troubleshooting clearly

V2 Scope
Included in V2
Simulated internet connectivity

Centralised internet breakout

NAT/PAT

OSPF default route advertisement

Centralised DHCP

DHCP relay

DNS

Active Directory

Domain-joined endpoints

Organisational Units

Users and security groups

Group Policy

Shared-resource permissions

Application server integration

Final service testing and validation

Outside the Scope of V2
Public cloud integration

Multi-domain Active Directory

Multiple domain controllers

Production internet connectivity

Public DNS hosting

Enterprise firewall appliances

VPN remote access

Wireless infrastructure

High-availability server clustering

These features are outside the intended scope of this portfolio lab.

Related Files
Topology
V2 Topology

Topology Overview

Configurations
Full Device Configurations

V2 Configuration Changes

Other Documentation
V1 Lab Documentation

Lab Documentation Overview

Enterprise Network Lab Overview

Main Portfolio README

Summary
V2 expands the completed CCNA-level network foundation from V1 into a more complete enterprise environment.

It demonstrates how internet access, address translation, centralised IP allocation, DNS, identity services, access control, Group Policy, and internal application services can be integrated into an existing multi-site network.

The completed V2 documentation will show not only the final configuration, but also the design reasoning, validation process, troubleshooting steps, and practical lessons learned during implementation.



01-internet-&-edge.md
File
Can you improve this markdown file so that it is in the same style as the V1 readmes.

Worked for 1m 32s
Replace the contents of enterprise-network-lab/labs/v2/01-internet-&-edge.md with the following:

01 - Internet Edge and NAT
Overview
This phase introduces simulated internet connectivity to the V2 Enterprise Network Lab.

The completed V1 network already provides internal routing between the headquarters, Engineering branch, and Sales branch. V2 extends that design by configuring HQ-R1 as the central internet edge router.

HQ-R1 provides:

A connection to the simulated public internet

A static default route towards the external network

Default route advertisement through OSPF

Network Address Translation

Port Address Translation for internal clients

A central internet egress point for all enterprise networks

Port Address Translation allows multiple devices using private IP addresses to share the public IP address assigned to the internet-facing interface on HQ-R1.

Objective
The objective of this phase is to provide controlled outbound connectivity from the private enterprise network to a simulated external network.

This includes:

Configuring an internet-facing interface on HQ-R1

Defining the NAT inside and NAT outside interfaces

Identifying the internal addresses eligible for translation

Configuring PAT using the HQ-R1 external interface

Configuring a static default route towards the external router

Advertising the default route into OSPF

Confirming that internal routers learn the default route

Verifying that NAT translations are created

Documenting the limitations of the simulated internet environment

Topology Reference
The screenshot below shows the V2 EVE-NG topology.



HQ-R1 connects the existing enterprise network to a separate router representing the public internet.

The private WAN/MPLS-style provider network remains responsible for connectivity between HQ and the two branch sites. The new public internet connection is a separate routed link connected directly to HQ-R1.

Relationship to V1
V1 provided complete internal enterprise connectivity but did not include an internet edge.

V2 introduces internet connectivity without redesigning the existing routing or switching architecture.

Area	V1	V2
Internal VLAN routing	Implemented	Retained
HQ and branch connectivity	Implemented	Retained
OSPF routing	Internal routes only	Extended with a default route
Private WAN	Implemented	Retained
Internet connectivity	Not included	Added through HQ-R1
NAT/PAT	Not included	Added
Public addressing	Not included	Simulated using 203.0.113.0/30
Internet egress	Not included	Centralised through HQ-R1
This demonstrates how internet access can be added to an existing routed enterprise network without changing the underlying internal addressing design.

Internet Edge Design
HQ-R1 acts as the boundary between the private enterprise network and the simulated public internet.

Component	Purpose
HQ-R1	Enterprise internet edge router
Internal interfaces	Receive traffic from HQ and branch networks
External interface	Connects HQ-R1 to the simulated public internet
NAT/PAT	Translates private source addresses
Static default route	Directs unknown destinations towards the external router
OSPF default advertisement	Distributes the default route internally
All enterprise networks use private 192.168.0.0/16 addressing.

The routed transit and private WAN links use 10.0.0.0/8 addressing.

Only the 192.168.0.0/16 enterprise LAN networks are selected for translation.

External Network Simulation
The external network is represented by a separate router in EVE-NG.

This router simulates an upstream internet provider and is outside the administrative boundary of the enterprise network.

The internet-facing connection uses:

Device	Interface	IP Address	Purpose
Public Internet Router	Connected interface	203.0.113.1/30	External next-hop
HQ-R1	GigabitEthernet0/3	203.0.113.2/30	Enterprise internet edge
The subnet used for the simulated connection is:

203.0.113.0/30
The /30 subnet provides two usable addresses:

203.0.113.1
203.0.113.2
This is sufficient for a point-to-point connection between HQ-R1 and the simulated public internet router.

Traffic Flow
Internet-bound traffic follows this path:

Internal client
    ↓
Local default gateway
    ↓
Existing OSPF routing domain
    ↓
OSPF-learned default route
    ↓
HQ-R1 NAT inside interface
    ↓
PAT translation
    ↓
HQ-R1 GigabitEthernet0/3
    ↓
Simulated public internet
When an internal client sends traffic towards an unknown external destination:

The client forwards the packet to its local default gateway.

The internal router or Layer 3 switch uses its OSPF-learned default route.

The packet is forwarded towards HQ-R1.

HQ-R1 receives the packet on a NAT inside interface.

The source address is checked against the NAT ACL.

The private source address is translated to 203.0.113.2.

A unique transport-layer port or ICMP identifier is used to distinguish the session.

The translated packet is forwarded through GigabitEthernet0/3.

For return traffic, HQ-R1 would use the NAT translation table to map the packet back to the original internal device.

HQ-R1 Interface Roles
The HQ-R1 interfaces are assigned the following NAT roles:

Interface	Connection	Address	NAT Role
GigabitEthernet0/0	Private WAN / ISP router	10.0.0.1/30	Inside
GigabitEthernet0/1	HQ-CSW1	10.0.1.2/30	Inside
GigabitEthernet0/2	HQ-CSW2	10.0.1.6/30	Inside
GigabitEthernet0/3	Simulated public internet	203.0.113.2/30	Outside
GigabitEthernet0/0 is configured as a NAT inside interface because traffic from the Engineering and Sales branch networks reaches HQ-R1 through the private WAN.

GigabitEthernet0/1 and GigabitEthernet0/2 are also NAT inside interfaces because they receive traffic from the HQ core switches.

NAT Address Classification
A standard ACL identifies the internal source addresses that are eligible for translation.

access-list 1 permit 192.168.0.0 0.0.255.255
This matches the following enterprise LAN networks:

Network	Purpose
192.168.10.0/24	Admin VLAN
192.168.20.0/24	Server VLAN
192.168.30.0/24	Engineering branch
192.168.40.0/24	Sales branch
The ACL deliberately does not match the 10.0.0.0/8 transit networks.

This prevents internal router-to-router traffic from being translated unnecessarily.

The NAT ACL classifies which source addresses should be translated. It is not being used as a traffic-filtering security ACL.

PAT Configuration
PAT is configured using the IP address assigned to GigabitEthernet0/3.

ip nat inside source list 1 interface GigabitEthernet0/3 overload
The overload keyword allows multiple internal devices to share the same outside global address.

In this lab, the shared outside global address is:

203.0.113.2
HQ-R1 distinguishes simultaneous sessions using port numbers or ICMP identifiers.

This is the same general approach used by many small and medium-sized networks where multiple private devices share a limited number of public IPv4 addresses.

Interface Configuration
NAT Inside Interfaces
interface GigabitEthernet0/0
 description TO PRIVATE WAN
 ip nat inside

interface GigabitEthernet0/1
 description TO HQ-CSW1
 ip nat inside

interface GigabitEthernet0/2
 description TO HQ-CSW2
 ip nat inside
These interfaces receive traffic originating from the internal enterprise network.

NAT Outside Interface
interface GigabitEthernet0/3
 description TO PUBLIC INTERNET
 ip address 203.0.113.2 255.255.255.252
 ip nat outside
 no shutdown
GigabitEthernet0/3 is the only NAT outside interface.

Traffic leaving this interface is translated when its source address matches ACL 1.

Default Route Configuration
HQ-R1 requires a default route for destinations that are not present in its routing table.

ip route 0.0.0.0 0.0.0.0 203.0.113.1
This route forwards unknown destinations to the simulated public internet router.

The routing table entry should appear as:

S* 0.0.0.0/0 via 203.0.113.1
The asterisk indicates that the route is a candidate default route.

OSPF Default Route Advertisement
The static default route exists only on HQ-R1.

To allow the rest of the enterprise network to use HQ-R1 for internet-bound traffic, the default route is advertised into OSPF.

router ospf 1
 default-information originate
The default-information originate command advertises a default route only while HQ-R1 has a default route in its local routing table.

This provides more appropriate behaviour than configuring individual static default routes on every internal router.

Internal routers can learn the default route dynamically and use HQ-R1 as the central internet gateway.

Expected Internal Routing Behaviour
After the default route is advertised:

HQ core switches learn an OSPF default route

HQ-R2 learns an OSPF default route

BR1 learns an OSPF default route

BR2 learns an OSPF default route

Unknown external destinations are forwarded towards HQ-R1

Internal enterprise routes continue to use the existing OSPF topology

An internal router should display an OSPF external default route similar to:

O*E2 0.0.0.0/0
The exact next-hop address depends on the device and its position within the OSPF topology.

Configuration Summary
The main HQ-R1 configuration added during this phase is:

access-list 1 permit 192.168.0.0 0.0.255.255

ip nat inside source list 1 interface GigabitEthernet0/3 overload

interface GigabitEthernet0/0
 ip nat inside

interface GigabitEthernet0/1
 ip nat inside

interface GigabitEthernet0/2
 ip nat inside

interface GigabitEthernet0/3
 description TO PUBLIC INTERNET
 ip address 203.0.113.2 255.255.255.252
 ip nat outside
 no shutdown

ip route 0.0.0.0 0.0.0.0 203.0.113.1

router ospf 1
 default-information originate
Verification Commands
The following commands can be used to verify the internet edge configuration.

Command	Purpose
show ip interface brief	Confirms that the internet-facing interface is operational
show ip route 0.0.0.0	Confirms the static default route on HQ-R1
show ip route ospf	Confirms OSPF-learned routes
show ip ospf database external	Confirms that the default route is advertised as an external OSPF route
show access-lists 1	Confirms the NAT classification ACL and match counters
show ip nat statistics	Displays NAT interface roles and translation statistics
show ip nat translations	Displays active NAT/PAT translation entries
clear ip nat translation *	Clears dynamic translations before repeating a controlled test
NAT Translation Verification
The following command was used on HQ-R1:

show ip nat translations
The output below shows that private internal source addresses were translated to the outside interface address on HQ-R1.

<img width="1792" height="670" alt="HQ-R1 NAT translation table" src="https://github.com/user-attachments/assets/7fa6cb96-7bdb-43bc-a625-bae12b1f0a3e" />

The translation table confirms that:

Traffic reached HQ-R1 from an internal network

The internal source address matched ACL 1

PAT used the GigabitEthernet0/3 address

A dynamic translation entry was created

Multiple internal sessions can share the same outside global address

Default Route Verification
The default route can be verified on HQ-R1 using:

show ip route 0.0.0.0
Expected behaviour:

HQ-R1 has a static default route

The next hop is 203.0.113.1

The route is installed in the routing table

HQ-R1 can advertise the route into OSPF

The complete routing table can also be reviewed using:

show ip route
OSPF Verification
Internal routers should learn the default route through OSPF.

This can be verified using:

show ip route 0.0.0.0
Expected behaviour on an internal OSPF router:

O*E2 0.0.0.0/0
This confirms that:

HQ-R1 originated the default route

OSPF distributed the route across the enterprise

Internal devices do not require individual static default routes

Internet-bound traffic is directed towards the central edge router

Test Summary
Test Area	Expected Result	Recorded Result
HQ-R1 external interface	Interface operational	Passed
Static default route	Route points to 203.0.113.1	Passed
OSPF default advertisement	Internal routers learn a default route	Passed
NAT address classification	Only 192.168.0.0/16 is translated	Passed
PAT translation creation	Dynamic translations appear on HQ-R1	Passed
End-to-end ICMP reply	Reply received from external destination	Not completed by the external simulation
Simulated Internet Limitation
During testing, HQ-R1 successfully created NAT translation entries for traffic sent towards the external network.

However, ICMP replies were not received from the simulated external environment.

The successful translation entries confirm that HQ-R1:

Received the internal traffic

Matched the correct private source address

Translated the source to 203.0.113.2

Forwarded the translated traffic towards the NAT outside interface

A successful translation entry does not, by itself, prove that the external destination returned the packet. The lack of a reply is therefore documented as a limitation of the current internet simulation rather than presented as a successful end-to-end internet test.

This distinction keeps the validation technically accurate.

Design Considerations
Selective Translation
Only the enterprise LAN range is selected for NAT:

192.168.0.0/16
The private 10.0.0.0/8 transit network is excluded.

This ensures that router-to-router traffic and OSPF infrastructure traffic are not translated.

Centralised Internet Egress
All internet-bound traffic exits through HQ-R1.

Benefits include:

A single location for NAT configuration

Simplified routing

Easier troubleshooting

Consistent outbound traffic flow

Centralised policy enforcement

PAT Address Conservation
PAT allows all internal enterprise devices to share one external IPv4 address.

This conserves public IPv4 address space and reflects a common real-world internet edge design.

Routing and NAT Separation
OSPF determines how traffic reaches HQ-R1.

NAT changes the source address as traffic crosses the internet boundary.

These are separate functions:

Routing selects the forwarding path

NAT translates the packet address

PAT distinguishes simultaneous sessions

Both must operate correctly for outbound connectivity to work.

Single Internet Edge Limitation
HQ-R1 is the only internet edge router in the current design.

If HQ-R1 or its external connection fails, internal routing between enterprise sites can continue, but simulated internet access becomes unavailable.

Internet edge redundancy is outside the current V2 scope.

Troubleshooting Approach
If NAT translations are not created, the following checks can be performed in order:

Confirm that the source client has a valid IP address and default gateway.

Confirm that the internal router has a default route towards HQ-R1.

Confirm that HQ-R1 has a route back to the client network.

Confirm that the packet enters a NAT inside interface.

Confirm that the source address matches ACL 1.

Confirm that GigabitEthernet0/3 is configured as ip nat outside.

Confirm that the static default route is installed.

Review show ip nat statistics.

Review show ip nat translations.

Clear existing translations and repeat the test if required.

Useful commands include:

show ip route
show ip ospf neighbor
show access-lists 1
show ip nat statistics
show ip nat translations
show ip interface brief
Observations
The completed configuration demonstrates that:

HQ-R1 operates as the central internet edge router

Internal enterprise networks are correctly classified for translation

Transit and WAN addresses are excluded from NAT

PAT uses the external interface address on HQ-R1

A static default route directs external traffic towards the simulated internet

The default route is distributed through OSPF

Internal routers can use HQ-R1 without individual static default routes

NAT translations are successfully created

The external simulation does not currently provide a complete return path for ICMP validation

Skills Demonstrated
This phase demonstrates practical skills relevant to junior network engineering roles, including:

Extending an existing routed network

Configuring an enterprise internet edge

Identifying NAT inside and outside interfaces

Implementing dynamic PAT overload

Writing a standard ACL for NAT classification

Excluding infrastructure networks from translation

Configuring static default routing

Advertising a default route through OSPF

Verifying NAT translation tables

Distinguishing translation success from end-to-end connectivity

Documenting lab limitations accurately

Troubleshooting routing and NAT as separate network functions

Outcome
HQ-R1 now provides a centralised internet edge for the V2 Enterprise Network Lab.

Internal devices from the Admin, Server, Engineering, and Sales networks can forward internet-bound traffic towards HQ-R1 using a default route distributed through OSPF.

HQ-R1 translates eligible private source addresses using PAT and forwards the traffic through its simulated public interface.

The successful creation of NAT translation entries confirms that the routing and translation configuration operates as intended. The absence of returned ICMP traffic is documented separately as a limitation of the current external network simulation.

This phase provides the routing and internet edge foundation required for the remaining V2 enterprise services.

This version retains the configuration and NAT evidence from your uploaded document while matching the structure and technical tone used throughout the V1 lab files. 




Alexis-Bll-main.zip
Zip Archive
Can you update my main readme. I have made my ccna project private (I sly can't be bothered to finish it.)

Worked for 1m 8s
I updated your profile README to:

Remove the link and featured section for the private CCNA project

Replace the outdated job-seeking wording

Present you as a Junior Network Engineer working in an MSP environment

Highlight your Cisco Meraki, Ruckus, WatchGuard, PRTG, Windows Server, Microsoft 365, VoIP, and troubleshooting experience

Retain your CCNA badge and degree

Add clearer technical skills and current-development sections




Library
/
Github Network Lab Portfolio
/
Alexis-Bll-README-updated.md


# Hi, I'm Alexis 👋

I am a UK-based **Junior Network Engineer** working in a managed service provider environment, supporting network and IT infrastructure across multi-site hospitality environments.

I hold a **First Class BSc in Forensic Computing & Security from Bournemouth University** and the **Cisco Certified Network Associate (CCNA)** certification. My current development is focused on Fortinet, Cisco Meraki, Windows Server, network monitoring, and practical infrastructure troubleshooting.

---

## Certifications

<a href="https://www.credly.com/badges/266127bb-dbe7-4faf-a2c9-eb2290d0bf49/public_url">
  <img src="ccna.png" width="180" alt="Cisco Certified Network Associate badge">
</a>

**Cisco Certified Network Associate (CCNA)**

Additional professional development includes Fortinet network-security training and 3CX certification.

---

## Current Role

In my role as a Junior Network Engineer, I support and troubleshoot live customer environments involving:

- LAN, WAN, VLAN, and wireless connectivity
- Cisco Meraki MX, MS, and MR infrastructure
- Ruckus wireless networks
- WatchGuard firewalls and remote-access VPNs
- Windows Server, Active Directory, and Microsoft 365
- PRTG monitoring and alert investigation
- Datto RMM and Autotask ticket management
- VoIP platforms including 3CX and Mitel
- Access-point, switch-port, cabling, printer, and endpoint issues
- Technical communication with customers, vendors, and on-site engineers

This experience is helping me develop practical troubleshooting, documentation, escalation, and customer-support skills in real production environments.

---

## Technical Skills

### Networking

- IPv4 addressing and subnetting
- VLANs and inter-VLAN routing
- OSPF
- Spanning Tree Protocol
- EtherChannel
- HSRP
- NAT and PAT
- ACLs
- DHCP and DNS
- DHCP Snooping, Dynamic ARP Inspection, and Port Security
- Wireless troubleshooting and RF configuration

### Platforms and Tools

- Cisco IOS
- Cisco Meraki Dashboard
- Fortinet FortiGate
- Ruckus
- WatchGuard
- EVE-NG
- Wireshark
- PRTG
- Datto RMM
- Autotask PSA
- Windows Server and Active Directory
- Microsoft 365
- VMware and Proxmox

---

## Education

**BSc (Hons) Forensic Computing & Security — First Class**  
Bournemouth University

My degree developed my understanding of:

- Digital forensics
- Cybersecurity principles
- Network security
- Incident investigation
- Secure infrastructure design
- Technical research and documentation

---

## What I'm Currently Developing

- Fortinet FortiGate administration and network security
- Cisco Meraki switching, wireless, and security appliances
- Enterprise wireless troubleshooting
- Firewall policies, NAT, and VPN technologies
- Windows Server and Active Directory administration
- Network monitoring and incident response
- Clear technical documentation for support and engineering teams

---

## Career Direction

My goal is to continue developing as a network engineer by gaining deeper hands-on experience with enterprise networking, wireless infrastructure, firewalls, monitoring, and network security.

I am particularly interested in roles and projects that combine structured troubleshooting, customer support, infrastructure improvement, and secure network design.
Library
/
Github Network Lab Portfolio
/
Alexis-Bll-README-updated.md


# Hi, I'm Alexis 👋

I am a UK-based **Junior Network Engineer** working in a managed service provider environment, supporting network and IT infrastructure across multi-site hospitality environments.

I hold a **First Class BSc in Forensic Computing & Security from Bournemouth University** and the **Cisco Certified Network Associate (CCNA)** certification. My current development is focused on Fortinet, Cisco Meraki, Windows Server, network monitoring, and practical infrastructure troubleshooting.

---

## Certifications

<a href="https://www.credly.com/badges/266127bb-dbe7-4faf-a2c9-eb2290d0bf49/public_url">
  <img src="ccna.png" width="180" alt="Cisco Certified Network Associate badge">
</a>

**Cisco Certified Network Associate (CCNA)**

Additional professional development includes Fortinet network-security training and 3CX certification.

---

## Current Role

In my role as a Junior Network Engineer, I support and troubleshoot live customer environments involving:

- LAN, WAN, VLAN, and wireless connectivity
- Cisco Meraki MX, MS, and MR infrastructure
- Ruckus wireless networks
- WatchGuard firewalls and remote-access VPNs
- Windows Server, Active Directory, and Microsoft 365
- PRTG monitoring and alert investigation
- Datto RMM and Autotask ticket management
- VoIP platforms including 3CX and Mitel
- Access-point, switch-port, cabling, printer, and endpoint issues
- Technical communication with customers, vendors, and on-site engineers

This experience is helping me develop practical troubleshooting, documentation, escalation, and customer-support skills in real production environments.

---

## Technical Skills

### Networking

- IPv4 addressing and subnetting
- VLANs and inter-VLAN routing
- OSPF
- Spanning Tree Protocol
- EtherChannel
- HSRP
- NAT and PAT
- ACLs
- DHCP and DNS
- DHCP Snooping, Dynamic ARP Inspection, and Port Security
- Wireless troubleshooting and RF configuration

### Platforms and Tools

- Cisco IOS
- Cisco Meraki Dashboard
- Fortinet FortiGate
- Ruckus
- WatchGuard
- EVE-NG
- Wireshark
- PRTG
- Datto RMM
- Autotask PSA
- Windows Server and Active Directory
- Microsoft 365
- VMware and Proxmox

---

## Education

**BSc (Hons) Forensic Computing & Security — First Class**  
Bournemouth University

My degree developed my understanding of:

- Digital forensics
- Cybersecurity principles
- Network security
- Incident investigation
- Secure infrastructure design
- Technical research and documentation

---

## What I'm Currently Developing

- Fortinet FortiGate administration and network security
- Cisco Meraki switching, wireless, and security appliances
- Enterprise wireless troubleshooting
- Firewall policies, NAT, and VPN technologies
- Windows Server and Active Directory administration
- Network monitoring and incident response
- Clear technical documentation for support and engineering teams

---

## Career Direction

My goal is to continue developing as a network engineer by gaining deeper hands-on experience with enterprise networking, wireless infrastructure, firewalls, monitoring, and network security.

I am particularly interested in roles and projects that combine structured troubleshooting, customer support, infrastructure improvement, and secure network design.
