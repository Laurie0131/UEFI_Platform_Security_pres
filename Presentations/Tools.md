---?image=assets/images/gitpitch-audience.jpg
@title[EDK II UDK Debugger]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI Newtwork in EDK II 

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Newtwork in EDK II Pres

  Copyright (c) 2018, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI  Network Stack Layers<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; host and target basic configuration and components</span> </li>
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;EDK II Network Features Overview </span></li>
 <li>@fa[certificate gp-bullet-gold]<span style="font-size:0.9em">&nbsp;&nbsp;What UEFI Protocols Make Network Work in EDK II </span> </li>
 <li>@fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI HTTP(s) Boot Overview </span></li>
</ul>

---?image=assets/images/binary-strings-black2.jpg
@title[Network Stack Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The Network Stack </span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Industry Standard on Networking</span>

Note:


---?image=/assets/images/slides/Slide4.JPG
<!-- .slide: data-transition="none" -->
@title[Network Stack Layers ]
<br>
<p align="center"><span class="gold" ><b>Industry Standard – Network Stack Layers </b></span></p>

Note:
### Open Systems Interconnection (OSI) is an effort to standardize networking that was started in 1977[1] by the International Organization for Standardization (ISO), 

- OSI Model is a reference model.
- TCP/IP Model roughly covers six layers of the OSI Reference Model with the TCP/IP Application layer as a compound of the Application, Presentation and Session layers in OSI Model.
- TCP/IP Model doesn’t cover the Physical/Hardware layer.
- The TCP/IP Model is familiar, UEFI network stack also follows this model. We will have a big picture on what we have now in each of the TCP/IP Model layers.




+++?image=/assets/images/slides/Slide5.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layers 02 ]
<br>
<p align="center"><span class="gold" ><b>Industry Standard – Network Stack Layers </b></span></p>

Note:
### Open Systems Interconnection (OSI) is an effort to standardize networking that was started in 1977[1] by the International Organization for Standardization (ISO), 

- OSI Model is a reference model.
- TCP/IP Model roughly covers six layers of the OSI Reference Model with the TCP/IP Application layer as a compound of the Application, Presentation and Session layers in OSI Model.
- TCP/IP Model doesn’t cover the Physical/Hardware layer.
- The TCP/IP Model is familiar, UEFI network stack also follows this model. We will have a big picture on what we have now in each of the TCP/IP Model layers.


+++?image=/assets/images/slides/Slide6.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layers 03 ]
<br>
<p align="center"><span class="gold" ><b>Industry Standard – Network Stack Layers </b></span></p>

Note:
### Open Systems Interconnection (OSI) is an effort to standardize networking that was started in 1977[1] by the International Organization for Standardization (ISO), 

- OSI Model is a reference model.
- TCP/IP Model roughly covers six layers of the OSI Reference Model with the TCP/IP Application layer as a compound of the Application, Presentation and Session layers in OSI Model.
- TCP/IP Model doesn’t cover the Physical/Hardware layer.
- The TCP/IP Model is familiar, UEFI network stack also follows this model. We will have a big picture on what we have now in each of the TCP/IP Model layers.


---?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-transition="none" -->
@title[TCP / IP Network Stack for UEFI  ]
<br>
<p align="center"><span class="gold" ><b>TCP / IP Network Stack for UEFI </b></span></p>

Note:

- So here we see the industry standard stack 
- Now add the UEFI Protocols to support this stack


+++?image=/assets/images/slides/Slide10.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[TCP / IP Network Stack for UEFI 02 ]
<br>
<p align="center"><span class="gold" ><b>TCP / IP Network Stack for UEFI </b></span></p>

Note:

Deferred Procedure Call - DPC

1. ICMP: Internet Control Message Protocol
2. MLD: Multicast Listener Discovery support
3. ND: Neighbor Discovery support



---?image=/assets/images/slides/Slide12.JPG
@title[Network Acronyms   ]
<p align="right"><span class="gold" ><b>Network Acronyms  </b></span></p>

Note:

- Address Resolution Protocol (ARP) is a telecommunications protocol used for resolution of network layer addresses into link layer addresses, a critical function in multiple-access networks. ARP was defined by RFC 826 in 1982.[1] It is Internet Standard STD 37. It is also the name of the program for manipulating these addresses in most operating systems.

- The Address Resolution Protocol is a request and reply protocol that runs encapsulated by the line protocol. It is communicated within the boundaries of a single network, never routed across internetwork nodes. This property places ARP into the Link Layer of the Internet Protocol Suite,[2] while in the Open Systems Interconnection (OSI) model, it is often described as residing between Layers 2 and 3, being encapsulated by Layer 2 protocols. However, ARP was not developed in the OSI framework.
- DPC _ allows high-priority tasks (e.g. an interrupt handler) to defer required but lower-priority tasks for later execution. This permits device drivers and other low-level event consumers to perform the high-priority part of their processing quickly, and schedule non-critical additional processing for execution at a lower priority.


- ICMP: Internet Control Message Protocol
- MLD: Multicast Listener Discovery support
- ND: Neighbor Discovery support
- IGMP Internet Group Management Protocol (IGMP) is a communications protocol used by hosts and adjacent routers on IPv4 networks to establish multicast group memberships. IGMP is an integral part of IP multicast.

#### Glossary: 

- MTFTP 	- Multicast Trivial File Transfer Protocol
- PXE 	– PreBoot eXecution Environment 
- DHCP 	- Dynamic Host Configuration Protocol
- iSCSI	- Internet Small Computer System Interface
- HTTP(s)	- HyperText Transfer Protocol w/  (s)-TLS
- TLS	- Transport Layer Security
- DNS	- Domain Name Server
- TCP 	- Transmission Control Protocol
- UDP 	- User Datagram Protocol
- IP 	- Internet Protocol 
- ARP	- Address Resolution Protocol 
- MNP 	– Managed Network Protocol 
- SNP 	– Simple Network Protocol
- UNDI 	- Universal Network Device Interface 
- DPC 	- Deferred Procedure Call  




---?image=/assets/images/slides/Slide14.JPG
@title[Network Stack Layout IPv4 ]
<p align="right"><span class="gold" ><b>Network Stack IPv4  </b></span></p>

Note:
 
Layout relationship IPv4

---?image=/assets/images/slides/Slide16.JPG
@title[Network Stack Layout IPv6 ]
<p align="right"><span class="gold" ><b>Network Stack IPv6  </b></span></p>

Note:
 
Layout relationship IPv6


---?image=/assets/images/slides/Slide18.JPG
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both ]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:
 
Layout relationship IPv4 or IPv6


+++?image=/assets/images/slides/Slide19.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 02]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:


+++?image=/assets/images/slides/Slide20.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 03]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:


+++?image=/assets/images/slides/Slide21.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 04]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide22.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 05]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide23.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 06]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide24.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 07]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide25.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 08]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide26.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 09]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide27.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 10]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide28.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 11]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

+++?image=/assets/images/slides/Slide29.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Network Stack Layout both 12]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

---?image=/assets/images/slides/Slide30.JPG
@title[Network Stack Layout both details]
<p align="right"><span class="gold" ><b>Network Stack IPv4 or IPv6  </b></span></p>

Note:

#### Caption Bullets From Left to right and down:
- Multicast Trivial File Transfer Protocol. Support multicast defined in RFC2090
- Dynamic Host Configuration Protocol. Typical usage: host automatic configuration
- HTTP(s): Hypertext Transfer Protocol over TLS, for secure network communication
- A transport method for SCSI, over TCP/IP networks.
- Core IPv6 functions: layer 3 unreliable transmission, routing, (de)fragmentation, integrated ICMP & MLD & ND  - Or Core IPv4  ICMP IGMP
   - ICMP: Internet Control Message Protocol
   - IGMP: Internet Group Management Protocol 
   - MLD: Multicast Listener Discovery support
   - ND: Neighbor Discovery support

- ARP - Resolve layer 3 addresses to layer 2 hardware addresses 
- Unreliable transport layer service. Datagram – data is transmitted in blocks
- Reliable transport layer service, more complex than UDP. Data is transmitted as a continuous stream.

- Provide concurrent access to frame-level functions. Multiplexer and de-multiplexer.
- Abstract interfaces of UNDI to packet level I/O & management interfaces.
- Network Interface Card Device Driver – Provide interfaces to operate the NIC.
- Not shown for IP Config V4/V6 - Used for configure and diagnose the IPv4 / IPv6 network stack



---?image=/assets/images/slides/Slide32.JPG
@title[UEFI Network Stack: IPv4 Vs. IPv6]
<p align="right"><span class="gold" ><b>UEFI Network Stack: IPv4 Vs. IPv6  </b></span></p>

Note:
This slide show the IPV4 and IPv6 side by side

- ICMP: Internet Control Message Protocol
- MLD: Multicast Listener Discovery support
- ND: Neighbor Discovery support
- IGMP Internet Group Management Protocol (IGMP) is a communications protocol used by hosts and adjacent routers on IPv4 networks to establish multicast group memberships. IGMP is an integral part of IP multicast.

#### Ping & IfConfig is used for configure and diagnose the IPv4 network stack.

- PXE over IPv6
	- Global address: Could be get from IPv6 stack
	- Boot file (DHCP4, header – bootfile & boot-file-option)
	- Next server address: (DHCP4 header include next server address)
	- NBP option (TBC)
- PXE
	- DHCP process: 
		- get ip address  - configure IPv4 stack
 		- next server address – setup communication /w PXE and-or server
	- PXE and-or server process:
		optional NBP choice (DHCP4 option convey these information)		download NBP




---?image=/assets/images/slides/Slide34.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Network Stack with Protocols]
<p align="right"><span class="gold" ><b>UEFI Network Stack with Protocols</b></span></p>

Note:

- This slide show the IPV4 and IPv6 side by side with Protocols
- iSCSI only allows one stack either IPv4 or IPv6
-   another Note: EFI_IP4_CONFIG_PROTOCOL has been deprecated and replaced with Ip4Config2 EFI_IP4_CONFIG2_PROTOCOL   , which has been implemented in Ip4Dxe driver

+++?image=/assets/images/slides/Slide35.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Network Stack with Protocols 02]
<p align="right"><span class="gold" ><b>UEFI Network Stack with Protocols</b></span></p>

Note:

- This slide show the IPV4 and IPv6 side by side with Protocols
- iSCSI only allows one stack either IPv4 or IPv6
-   another Note: EFI_IP4_CONFIG_PROTOCOL has been deprecated and replaced with Ip4Config2 EFI_IP4_CONFIG2_PROTOCOL   , which has been implemented in Ip4Dxe driver


+++?image=/assets/images/slides/Slide36.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Network Stack with Protocols 03]
<p align="right"><span class="gold" ><b>UEFI Network Stack with Protocols</b></span></p>

Note:

- This slide show the IPV4 and IPv6 side by side with Protocols
- iSCSI only allows one stack either IPv4 or IPv6
-   another Note: EFI_IP4_CONFIG_PROTOCOL has been deprecated and replaced with Ip4Config2 EFI_IP4_CONFIG2_PROTOCOL   , which has been implemented in Ip4Dxe driver

#### UEFI 2.5 added HTTP(s) Boot


---?image=/assets/images/slides/Slide38.JPG
@title[UEFI Network Stack Live Picture]
<p align="right"><span class="gold" ><b>UEFI Network Stack Live Picture</b></span></p>

Note:

- How can the 2 network protocols be managed 
- Here is a pictorial of a block diagram of the different layers with the different protocols


---?image=assets/images/binary-strings-black2.jpg
@title[EDK II Network Features Overview Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II Network</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II Network Features Overview</span>

Note:


---?image=/assets/images/slides/Slide41.JPG
@title[Where is the EDK II Network Stack located?]
<p align="right"><span class="gold" ><b>Where is the EDK II Network Stack located?</b></span></p>
<br>
@fa[github gp-bullet-black]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/">github.com/tianocore/edk2/ </a>

Note:
3 places depending on IP4 or IP6
- IP4:
  - MdeModulePkg
    - Universal
     - Network 

- IP6:
  - NetworkPkg

- Network Related Libraries
    - MdeModulePkg
      - Library



---?image=/assets/images/slides/Slide43.JPG
@title[How to Enable the EDK II Network Stack?]
<p align="right"><span class="gold" ><b>How to Enable the EDK II Network Stack</b></span></p>
<br>

<div class="left1">
<span style="font-size:0.8em" > Update the Platform DSC and FDF files:</span><br><br>
<span style="font-size:0.8em" >Wiki link: @fa[github gp-bullet-white]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/tianocore.github.io/wiki/NetworkPkg-Getting-Started-Guide#features-enabling  "> Featues enabling </a></span><br>
<pre>
```

DEFINE NETWORK_ENABLE  = TRUE
DEFINE NETWORK_IP6_ENABLE = TRUE
// . . .
```
</pre>
</div>
<div class="right1">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>

Note:


---?image=/assets/images/slides/Slide45.JPG
@title[IP6 Networking - Vendors]
<p align="right"><span class="gold" ><b>IP6 Networking - Vendors</b></span></p>
<br>

<div class="left">
<span style="font-size:0.8em" > IPv6 protocols compliance</span>
<ul>
 <li><span style="font-size:0.7em" >IPv6 ready logo approved <a href="http://www.ipv6ready.org/db/index.php/public/">ipv6ready.org</a> </span></li>
 <li><span style="font-size:0.7em" >Requirements for IPv6 transition  <a href="https://www.nist.gov/sites/default/files/documents/itl/antd/usgv6-v1.pdf">usgv6-v1.pdf</a> </span></li>
 <li><span style="font-size:0.7em" >Vendor Testing:  <a href="https://www-x.antd.nist.gov/usgv6/faq-c.html#vendors">faq-c.html#vendors  </a> </span></li>
</ul>
</div>
<div class="right">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>

Note:

- IPv6 UEFI 2.4 B 2011


---?image=/assets/images/slides/Slide47.JPG
<!-- .slide: data-transition="none" -->
@title[Virtual LAN  - VLAN]
<p align="center"><span class="gold" ><b>Virtual LAN  - VLAN</b></span></p>
<br>
<br>
<br>
<span style="font-size:0.6em" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <a href="http://www.cse.wustl.edu/~jain/cis788-97/ftp/virtual_lans/#WhatVLAN">Link</a> </span>


Note:

- What are VLAN's? http://www.cse.wustl.edu/~jain/cis788-97/ftp/virtual_lans/#ContentsTable 

- http://www.cisco.com/en/US/docs/ios/lanswitch/configuration/guide/lsw_rtng_vlan_ovw_ps6350_TSD_Products_Configuration_Guide_Chapter.html 

- A VLAN is a switched network that is logically segmented on an organizational basis, by functions, project teams, or applications rather than on a physical or geographical basis. For example, all workstations and servers used by a particular workgroup team can be connected to the same VLAN, regardless of their physical connections to the network or the fact that they might be intermingled with other teams. Reconfiguration of the network can be done through software rather than by physically unplugging and moving devices or wires.

- A VLAN can be thought of as a broadcast domain that exists within a defined set of switches. A VLAN consists of a number of end systems, either hosts or network equipment (such as bridges and routers), connected by a single bridging domain. The bridging domain is supported on various pieces of network equipment; for example, LAN switches that operate bridging protocols between them with a separate bridge group for each VLAN.
- VLANs are created to provide the segmentation services traditionally provided by routers in LAN configurations. VLANs address scalability, security, and network management. Routers in VLAN topologies provide broadcast filtering, security, address summarization, and traffic flow management. None of the switches within the defined group will bridge any frames, not even broadcast frames, between two VLANs. 

- VLAN's allow a network manager to logically segment a LAN into different broadcast domains (). Since this is a logical segmentation and not a physical one, workstations do not have to be physically located together. Users on different floors of the same building, or even in different buildings can now belong to the same LAN.
- VLAN's also allow broadcast domains to be defined without using routers. Bridging software is used instead to define which workstations are to be included in the broadcast domain. Routers would only have to be used to communicate between two VLAN's


- A virtual switch may be configured as either VLAN-aware or VLAN-unaware. This configuration option defines the behavior of the virtual switch when operating in a LAN segment that may be virtually segmented by VLANs. The virtual switch accepts all packets and frames and passes them to its ingress rules processing whether they are tagged or not. The virtual switch's VLAN support is based on the IEEE 802.1Q specification and governs how the virtual switch processes frames or packets that are VLAN tagged:


#### VLAN-unaware
- The virtual switch ignores VLAN tags in frames or packets. Essentially, 
the virtual LAN segment that may have been defined by another switch 
is not recognized. Frames and packets are filtered and delivered by 
their destination MAC or IP address. Any VLAN tagging that exists 
is ignored and remains in the frame. The virtual switch does not strip 
the tag from the frames (Ethernet mode), so if the virtual switch 
receives a tagged frame, the frame is delivered tagged to the destination 
MAC. This includes traffic destined for remote hosts through the OSA-Express 
trunk port. Tagged traffic flows unimpeded through the virtual switch 
to guest virtual machines and the OSA-Express trunk connection. 
It is recommended that hardware switch port that is connected to the 
OSA-Express port be configured as an access port. This insures that 
the virtual switch only processes traffic for the VLAN that has been 
configured on the hardware switch access port.



#### VLAN-aware

- The virtual switch enforces the VLAN defined topology constructed 
by the LAN administrator. The virtual switch uses the VLAN tagging 
in conjunction with the IP or Ethernet address for delivery of packets 
or frames. The port type definition for the destination MAC determines 
whether the frames are delivered (tagged or untagged). All inbound 
(ingress) and outbound (egress) frames or packets are processed according 
to the defined rules. |The virtual switch supports one untagged VLAN LAN segment 
of which the OSA-Express trunk port and those guest trunk ports 
which have been explicitly granted the designated native VLAN ID are 
members.
 VLAN construction and assignments are a manual process for 
the virtual switch through z/VM CP commands or an ESM. The virtual 
switch's native VLAN ID is set with the DEFINE VSWITCH command. 
Beginning in z/VM Release 5.2.0, the OSA-Express associated with a 
VLAN-aware virtual switch becomes a participant or an end station 
in a GVRP network. VLAN topology changes must be implemented statically 
using the SET VSWITCH command, the MODIFY VSWITCH system configuration 
statement, or an ESM. That configuration is propagated to the hardware 
switch, eliminating the need for manual configuration. 

#### The hardware 
- switch port that is connected to the OSA-Express port must be configured 
as a trunk port. This insures that the virtual switch receives VLAN 
traffic for all VLANs that have been configured for the virtual guest 
ports.



+++?image=/assets/images/slides/Slide48.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Virtual LAN  - VLAN 02]
<p align="center"><span class="gold" ><b>Virtual LAN  - VLAN</b></span></p>
<br>
<br>
<br>
<span style="font-size:0.6em" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <a href="http://www.cse.wustl.edu/~jain/cis788-97/ftp/virtual_lans/#WhatVLAN">Link</a> </span>


Note:



+++?image=/assets/images/slides/Slide49.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Virtual LAN  - VLAN 03]
<p align="center"><span class="gold" ><b>Virtual LAN  - VLAN</b></span></p>
<br>
<br>
<br>
<span style="font-size:0.6em" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <a href="http://www.cse.wustl.edu/~jain/cis788-97/ftp/virtual_lans/#WhatVLAN">Link</a> </span>


Note:



+++?image=/assets/images/slides/Slide50.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Virtual LAN  - VLAN 04]
<p align="center"><span class="gold" ><b>Virtual LAN  - VLAN</b></span></p>
<br>
<br>
<br>
<span style="font-size:0.6em" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <a href="http://www.cse.wustl.edu/~jain/cis788-97/ftp/virtual_lans/#WhatVLAN">Link</a> </span>



Note:



+++?image=/assets/images/slides/Slide51.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Virtual LAN  - VLAN 05]
<p align="center"><span class="gold" ><b>Virtual LAN  - VLAN</b></span></p>
<br>
<br>
<br>
<span style="font-size:0.6em" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <a href="http://www.cse.wustl.edu/~jain/cis788-97/ftp/virtual_lans/#WhatVLAN">Link</a> </span>



Note:




---?image=/assets/images/slides/Slide53.JPG
@title[VLAN Support - EDK II]
<p align="center"><span class="gold" ><b>VLAN Support - EDK II</b></span></p>
<br>

Note:

- Technology includes
  - Support Hybrid LAN topology
  - Multiple VLAN for one station
  - MNP and  VLAN Configuration Protocol
  - VLAN configuration by Shell Application Vconfig


#### How VLAN's work
- When a LAN bridge receives data from a workstation, it tags the data with a VLAN identifier indicating the VLAN from which the data came. This is called explicit tagging. It is also possible to determine to which VLAN the data received belongs using implicit tagging. In implicit tagging the data is not tagged, but the VLAN from which the data came is determined based on other information like the port on which the data arrived. Tagging can be based on the port from which it came, the source Media Access Control (MAC) field, the source network address, or some other field or combination of fields. VLAN's are classified based on the method used. 
- To be able to do the tagging of data using any of the methods, the bridge would have to keep an updated database containing a mapping between VLAN's and whichever field is used for tagging. For example, if tagging is by port, the database should indicate which ports belong to which VLAN. This database is called a filtering database. Bridges would have to be able to maintain this database and also to make sure that all the bridges on the LAN have the same information in each of their databases. The bridge determines where the data is to go next based on normal LAN operations. Once the bridge determines where the data is to go, it now needs to determine whether the VLAN identifier should be added to the data and sent. 
#### Aware
If the data is to go to a device that knows about VLAN implementation (VLAN-aware), the VLAN identifier is added to the data. 

####Unaware
- If it is to go to a device that has no knowledge of VLAN implementation (VLAN-unaware), the bridge sends the data without the VLAN identifier.
- In order to understand how VLAN's work, we need to look at the types of VLAN's, the types of connections between devices on VLAN's, the filtering database which is used to send traffic to the correct VLAN, and tagging, a process used to identify the VLAN originating the data.
- VLAN Standard: IEEE 802.1Q Draft Standard
- There has been a recent move towards building a set of standards for VLAN products. The Institute of Electrical and Electronic Engineers (IEEE) is currently working on a draft standard 802.1Q for VLAN's. Up to this point, products have been proprietary, implying that anyone wanting to install VLAN's would have to purchase all products from the same vendor. Once the standards have been written and vendors create products based on these standards, users will no longer be confined to purchasing products from a single vendor. The major vendors have supported these standards and are planning on releasing products based on them. 

- A virtual switch may be configured as either VLAN-aware or VLAN-unaware. This configuration option defines the behavior of the virtual switch when operating in a LAN segment that may be virtually segmented by VLANs. The virtual switch accepts all packets and frames and passes them to its ingress rules processing whether they are tagged or not. The virtual switch's VLAN support is based on the IEEE 802.1Q specification and governs how the virtual switch processes frames or packets that are VLAN tagged:



---?image=/assets/images/slides/Slide55.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI iSCSI Solutions]
<p align="center"><span class="gold" ><b>UEFI iSCSI Solutions</b></span></p>
<br>

Note:

- iSCSI is extremely versatile,  it allows you to send SCSI Storage commands over a ethernet Network or Internet
- Swiss army knife of networking because of its versatility 

#### Uses

1. To do Storage consolidation for application servers
Instead of loading up application servers with several disks, you can build 1 centralized storage server and link all your applications servers to it using iSCSI

2.  Build a low cost SAN – iSCSI is a lot less expensive then Fabre channel 
3.  You can use iSCSI for Clustering – you can build a Cluster Shared Volume around iSCSI
4.  Diskless Booting of servers

- iSCSI is a transport layer protocol that describes how Small Computer System Interface (SCSI) packets should be transported over a TCP/IP network.
- allows the SCSI command to be sent end-to-end over local-area networks (LANs), wide-area networks (WANs) or the Internet.

- How ISCSI works
- iSCSI works by transporting block-level data between an iSCSI initiator on a server and an iSCSI target on a storage device. The iSCSI protocol encapsulates SCSI commands and assembles the data in packets for the TCP/IP layer. Packets are sent over the network using a point-to-point connection. Upon arrival, the iSCSI protocol disassembles the packets, separating the SCSI commands so the operating system (OS) will see the storage as a local SCSI device that can be formatted as usual. Today, some of iSCSI's popularity in small to midsize businesses (SMBs) has to do with the way server virtualization makes use of storage pools. In a virtualized environment, the storage pool is accessible to all the hosts within the cluster and the cluster nodes nodes communicate with the storage pool over the network through the use of the iSCSI protocol.

- http://searchstorage.techtarget.com/definition/iSCSI 


- Challenge-Handshake Authentication Protocol (CHAP) 
  - Functions :
   - function checks the received iSCSI Login Response during the security negotiation stage.
   - function fills the CHAP authentication information into the login PDU during the security negotiation stage in the iSCSI connection login.

- You can use CHAP authentication to restrict iSCSI access to volumes and snapshots to hosts that supply the correct account name and password (or "secret") combination.
- Using CHAP authentication can facilitate the management of access controls because it restricts access through account names and passwords, instead of IP addresses or iSCSI initiator names.



+++?image=/assets/images/slides/Slide56.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI iSCSI Solutions 02]
<p align="center"><span class="gold" ><b>UEFI iSCSI Solutions</b></span></p>
<br>

Note:



+++?image=/assets/images/slides/Slide58.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI iSCSI Solutions 03]
<p align="center"><span class="gold" ><b>UEFI iSCSI Solutions</b></span></p>
<br>

Note:

- EDK II Menu for setting up iSCSI




---?image=/assets/images/slides/Slide60.JPG
@title[Dual-Stack Heritage – iSCSI usage model EDK II]
<p align="center"><span class="gold" ><b>Dual-Stack Heritage – iSCSI usage model EDK II</b></span></p>
<br>

Note:
iSCSI can be either IPv4 or IPv6 with EDK II 




---?image=/assets/images/slides/Slide62.JPG
<!-- .slide: data-transition="none" -->
@title[IPsec – Network Security]
<p align="center"><span class="gold" ><b>IPsec – Network Security</b></span></p>
<br>

Note:
- Internet Protocol Security (IPsec) is a protocol suite for secure Internet Protocol (IP) communications that works by authenticating and encrypting each IP packet of a communication session. IPsec includes protocols for establishing mutual authentication between agents at the beginning of the session and negotiation of cryptographic keys to be used during the session. 
- IPsec can be used in protecting data flows between a pair of hosts (host-to-host), between a pair of security gateways (network-to-network), or between a security gateway and a host (network-to-host).[1] Internet Protocol security (IPsec) uses cryptographic security services to protect communications over Internet Protocol (IP) networks. IPsec supports network-level peer authentication, data origin authentication, data integrity, data confidentiality (encryption), and replay protection.

- IPsec is an end-to-end security scheme operating in the Internet Layer of the Internet Protocol Suite, 
- Only IPsec protects all application traffic over an IP network. Applications can be automatically secured by IPsec at the IP layer.

#### AH
- AH -Authentication Headers (AH) provide connectionless data integrity and data origin authentication for IP datagrams and provides protection against replay attacks

#### ESP
- Encapsulating Security Payloads (ESP) provide confidentiality, data-origin authentication, connectionless integrity, an anti-replay service (a form of partial sequence integrity), and limited traffic-flow confidentiality.


#### IKE IKEv2
- Internet Key Exchange (IKE, sometimes IKEv1 or IKEv2) is the protocol used to set up a security association (SA) in the IPsec protocol suite. IKE builds upon the Oakley protocol and ISAKMP.[1] IKE uses X.509 certificates for authentication - either pre-shared or distributed using DNS (preferably with DNSSEC) and a Diffie–Hellman key exchange - to set up a shared session secret from which cryptographic keys are derived.
- In addition, a security policy for every peer which will connect must be manually maintained

#### HMAC-SHA1 
- Hash-based message authentication code – 
- SHA-1 produces a 160-bit (20-byte) hash value known as a message digest

#### TripleDES  w/ CBC
- Triple Data Encryption Algorithm (TDEA or Triple DEA), is a symmetric-key block cipher, which applies the Data Encryption Standard (DES) cipher algorithm three times to each data block.

- The original DES cipher's key size of 56 bits was generally sufficient when that algorithm was designed, but the availability of increasing computational power made brute-force attacks feasible. Triple DES provides a relatively simple method of increasing the key size of DES to protect against such attacks, without the need to design a completely new block cipher algorithm.

- Cipher Block Chaining (CBC) mode of operation founded in 1976. In CBC mode, each block of plaintext is XORed with the previous ciphertext block before being encrypted. This way, each ciphertext block depends on all plaintext blocks processed up to that point. To make each message unique, an initialization vector must be used in the first block.

#### AES-CBC
- Advanced Encryption Standard (AES), also known as Rijndael(its original name), is a specification for the encryption of electronic data established by the U.S. National Institute of Standards and Technology (NIST) in 2001
- The algorithm described by AES is a symmetric-key algorithm, meaning the same key is used for both encrypting and decrypting the data.


#### Modes of operation
- IPsec can be implemented in a host-to-host transport mode, as well as in a network tunneling mode.

#### Transport mode
- In transport mode, only the payload of the IP packet is usually encrypted or authenticated. The routing is intact, since the IP header is neither modified nor encrypted; however, when the authentication header is used, the IP addresses cannot be modified by network address translation, as this always invalidates the hash value. The transport and application layers are always secured by a hash, so they cannot be modified in any way, for example by translating the port numbers.

- A means to encapsulate IPsec messages for network address translation (NAT) traversal has been defined by RFC documents describing the NAT-T mechanism.
- NAT traversal is not supported with the transport mode.

#### Tunnel mode
- In tunnel mode, the entire IP packet is encrypted and authenticated. It is then encapsulated into a new IP packet with a new IP header. Tunnel mode is used to create virtual private networks (VPN) for network-to-network communications (e.g. between routers to link sites), host-to-network communications (e.g. remote user access) and host-to-host communications (e.g. private chat)

- Tunnel mode supports network address translation (NAT)-  traversal.

#### PURPOSE:
- Interoperability

+++?image=/assets/images/slides/Slide63.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IPsec – Network Security 02]
<p align="center"><span class="gold" ><b>IPsec – Network Security</b></span></p>
<br>

Note:


+++?image=/assets/images/slides/Slide64.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IPsec – Network Security 03]
<p align="center"><span class="gold" ><b>IPsec – Network Security</b></span></p>
<br>

Note:

+++?image=/assets/images/slides/Slide65.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IPsec – Network Security 04]
<p align="center"><span class="gold" ><b>IPsec – Network Security</b></span></p>
<br>

Note:

+++?image=/assets/images/slides/Slide66.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IPsec – Network Security 05]
<p align="center"><span class="gold" ><b>IPsec – Network Security</b></span></p>
<br>

Note:

+++?image=/assets/images/slides/Slide67.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IPsec – Network Security 06]
<p align="center"><span class="gold" ><b>IPsec – Network Security</b></span></p>
<br>

Note:

- Slide shows Authenticated and encrypted between the 2 modes



---?image=/assets/images/slides/Slide70.JPG
<!-- .slide: data-transition="none" -->
@title[IPsec support: shared]
<p align="right"><span class="gold" ><b>IPsec support: shared</b></span></p>
<br>

Note:
- EDK 2 IPsec Support Stack


+++?image=/assets/images/slides/Slide71.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IPsec support: shared 02]
<p align="right"><span class="gold" ><b>IPsec support: shared</b></span></p>
<br>

Note:

- EDK 2 IPsec Support Stack


---?image=/assets/images/slides/Slide73.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI PXE Solutions]
<p align="right"><span class="gold" ><b>UEFI PXE Solutions</b></span></p>
<br>

Note:

- Preboot eXecution Environment
  - General network booting
     - Independent of data storage device
  - IPv4 based PXE is defined in PXE 2.1
  - IPv6 based PXE is defined in UEFI 2.3
- Technology includes
  - Dual network stack support
    - Evolution of network boot to IPv6 defined in -  IETF RFC 5970
  - DUID-UUID support
    - Use SMBIOS system GUID as UUID


+++?image=/assets/images/slides/Slide74.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI PXE Solutions]
<p align="right"><span class="gold" ><b>UEFI PXE Solutions</b></span></p>
<br>

Note:
#### BUT
- Preboot eXecution Environment
  - General network booting
     - Independent of data storage device
  - IPv4 based PXE is defined in PXE 2.1
  - IPv6 based PXE is defined in UEFI 2.3
- Technology includes
  - Dual network stack support
    - Evolution of network boot to IPv6 defined in -  IETF RFC 5970
  - DUID-UUID support
    - Use SMBIOS system GUID as UUID


+++?image=/assets/images/slides/Slide75.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI PXE Solutions]
<p align="right"><span class="gold" ><b>UEFI PXE Solutions</b></span></p>
<br>

Note:
#### BUT PXE is not keeping up with modern data center needs



---?image=/assets/images/slides/Slide77.JPG
@title[PXE Boot Challenges]
<p align="right"><span class="gold" ><b>PXE Boot Challenges</b></span></p>
<br>


Note:

- Old technology WFM – 

- Scaling
  - not reliable
  
  - new era of Big data and deployment


- Work around
  - ipxe  or mini-OS


- Pxe not keepup

- iPXE 

- before UEFI 2.5 

- iPXE (http://ipxe.org) before UEFI 2.5
- Open-source PXE client and bootloader
  - –Required chain loading (PXE boot to iPXEthen run iPXEto HTTP download)
   - Adds support of HTTP Boot:
   –Used to only work with traditional BIOS, users have to choose between HTTP Boot and UEFI Secure Boot
   –Used to only provides low-level SNP interface (no HTTP Boot) in UEFI
   –Recently “the iPXEUEFI vision has mostly been implemented”
   –Not part of the UEFI standard
- iPXEUEFI vision
    –“Provide the same advanced features within the UEFI environment as are currently provided within the Traditional BIOS environment” -http://ipxe.org/efi/vision 


	

---?image=/assets/images/slides/Slide79.JPG
@title[HTTP(s) Boot Solutions]
<p align="center"><span class="gold" ><b>HTTP(s) Boot Solutions</b></span></p>
<br>

Note:
- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec


- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6
- RAM Disk
- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT)




+++?image=/assets/images/slides/Slide80.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP(s) Boot Solutions 02]
<p align="center"><span class="gold" ><b>HTTP(s) Boot Solutions</b></span></p>
<br>

Note:
- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec


- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6
- RAM Disk
- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT)


+++?image=/assets/images/slides/Slide81.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP(s) Boot Solutions 03]
<p align="center"><span class="gold" ><b>HTTP(s) Boot Solutions</b></span></p>
<br>

Note:
- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec


- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6
- RAM Disk
- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT)


+++?image=/assets/images/slides/Slide82.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP(s) Boot Solutions 04]
<p align="center"><span class="gold" ><b>HTTP(s) Boot Solutions</b></span></p>
<br>

Note:
- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec


- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6
- RAM Disk
- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT)


+++?image=/assets/images/slides/Slide83.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP(s) Boot Solutions 05]
<p align="center"><span class="gold" ><b>HTTP(s) Boot Solutions</b></span></p>
<br>

Note:
- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec


- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6
- RAM Disk
- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT)


+++?image=/assets/images/slides/Slide84.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP(s) Boot Solutions 06]
<p align="center"><span class="gold" ><b>HTTP(s) Boot Solutions</b></span></p>
<br>

Note:
#### HTTP UEFI 2.5 2015

- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec


- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6
- RAM Disk
- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT)



---?image=assets/images/binary-strings-black2.jpg
@title[EDK II  UEFI Protocols Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II  UEFI Protocols</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;What UEFI Protocols Make Network Work </span><br>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="font-size:0.7em" >- A deeper dive into the Network implementation in EDK II</span>

Note:


---?image=/assets/images/slides/Slide87.JPG
@title[UEFI Driver - Problem Statement]
<br>
<p align="center"><span class="gold" ><b>UEFI Driver - Problem Statement</b></span></p>
<br>
<br>
<ul>
<li><span style="font-size:0.9em" >The original UEFI Driver Model is not complete</span></li>
<li><span style="font-size:0.9em" >Good support for HW Device Driver</span></li>
<li><span style="font-size:0.9em" >Good support for HW Bus/Hybrid Driver</span></li>
<li><span style="font-size:0.9em" >Good support for Simple SW Layering driver</span></li>
<li><span style="font-size:0.9em" >Poor support for complex SW Layering driver</span></li>
</ul>

Note:

#### Same as slide
- The original UEFI Driver Model is not complete
- Good support for HW Device Driver
- Good support for HW Bus/Hybrid Driver
- Good support for Simple SW Layering driver
- Poor support for complex SW Layering driver


---?image=/assets/images/slides/Slide89.JPG
@title[UEFI Hardware  Device Driver]
<br>
<p align="center"><span class="gold" ><b>UEFI Hardware  Device Driver</b></span></p>
<br>

Note:

- UEFI Driver 101
- Graphics   PCI Device Driver


---?image=/assets/images/slides/Slide91.JPG
@title[UEFI Hardware Bus/Hybrid Driver]
<p align="center"><span class="gold" ><b>UEFI Hardware Bus/Hybrid Driver</b></span></p>
<br>

Note:

- UEFI Driver 101
- UEFI Hardware Bus/Hybrid Driver - SCSI Driver example




---?image=/assets/images/slides/Slide93.JPG
@title[UEFI Simple Software Driver]
<p align="center"><span class="gold" ><b>UEFI Simple Software Driver</b></span></p>
<br>

Note:

- UEFI Driver 101
- UEFI UEFI Simple Software Driver - FAT Driver - PXE Driver




---?image=/assets/images/slides/Slide95.JPG
<!-- .slide: data-transition="none" -->
@title[Complex Software Drivers]
<p align="center"><span class="gold" ><b>Complex Software Drivers</b></span></p>
<br>

Note:


+++?image=/assets/images/slides/Slide96.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Complex Software Drivers]
<p align="center"><span class="gold" ><b>Complex Software Drivers</b></span></p>
<br>

Note:
- Multiple Consumers


+++?image=/assets/images/slides/Slide97.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Complex Software Drivers]
<p align="center"><span class="gold" ><b>Complex Software Drivers</b></span></p>
<br>

Note:
- Notice the interacations around the red circles on this slide



---
@title[Complex Software Drivers]
<br>
<p align="center"><span class="gold" ><b>Complex Software Drivers</b></span></p>
<br>
<ul>
<li><span style="font-size:0.9em" >OpenProtocol() BY_DRIVER does not support sharing of protocol interfaces</span></li>
<li><span style="font-size:0.9em" >Number of Children is not fixed</span></li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Different than enumerable Hardware busses (PCI, ISA)</span></li>
    <li><span style="font-size:0.7em" >Similar to hot plug Hardware buses (USB)</span></li>
  </ul>

<li><span style="font-size:0.9em" >Must support Load/Unload at the Network Service Level</span></li>
<li><span style="font-size:0.9em" >Must support Connect/Disconnect at the Network Service Level</span></li>
</ul>

Note:


- Add Sharing to the Existing UEFI Drivers model
- Update UEFI Driver Model to support sharing
- Requires Architectural Change to UEFI:
  - InstallProtocolInterface()
  - InstallMultipleProtocolInterfaces()
- Pros
  - Simple
- Cons
  - Breaks compatibility and increases complexity of drivers to check EFI version


---?image=/assets/images/slides/Slide100.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Service Binding Protocol]
<p align="center"><span class="gold" ><b>UEFI Service Binding Protocol</b></span></p>
<br>

Note:
- UEFI Service Binding Protocol For Multiple Consumer scenario 

  

+++?image=/assets/images/slides/Slide101.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Service Binding Protocol]
<p align="center"><span class="gold" ><b>UEFI Service Binding Protocol</b></span></p>
<br>

Note:
- UEFI Service Binding Protocol For Multiple Consumer scenario 



---?image=/assets/images/slides/Slide107.JPG

@title[UEFI Service Binding Protocol ]
<p align="center"><span class="gold" ><b>UEFI Service Binding Protocol</b></span><span style="font-size:0.8em" ><br>– Complex Software Service Drivers</span></p>
<br>

Note:
- The UEFI Service Binding Protocol - Works as the Object Factory method for UEFI network stack drivers.
  - Object Factory is normally a class (object) whose primary function is to create objects of another class. The object created usually has concrete services requesters are interested in.
- One nature of network applications: concurrency, the multiple instances usage model.
- The mechanism is like EFI Simple File System Protocol, despite some minor differences.
  - SFS.OpenVolume () produces a new EFI File Protocol instance and directly OUTPUT it. Any subsequent operation is done via the EFI File Protocol instance.
  - SB.CreateChild () produces a new I/O protocol on the ChildHandle (either existing or new created one by core depending the initial value passed in). Requesters have to open the I/O protocol on the ChildHandle by himself.
  - SB.DestroyChild () must be called to clean up the object previous created and identified by the ChildHandle.


- Object Factory Method is a software design methodology from object-oriented programming  - which means this is a method  for creating a new object-interface where the creator of object will have a common interface.

---
@title[UEFI Service Binding Protocol code]
<br>
<p align="center"><span class="gold" ><b>UEFI Service Binding Protocol</b></span></p>
<br>
<span style="font-size:0.9em" >Code Example</span>
<br>
<div class="left">
<pre>
```
typedef struct _EFI_SERVICE_BINDING_PROTOCOL {
  EFI_SERVICE_BINDING_CREATE_CHILD   CreateChild;
  EFI_SERVICE_BINDING_DESTROY_CHILD DestroyChild;
} EFI_SERVICE_BINDING_PROTOCOL;
EFI_STATUS

```
</pre>
</div>
<div class="right1">
<pre>
```
EFI_STATUS
(EFIAPI *EFI_SERVICE_BINDING_CREATE_CHILD) (
  IN EFI_SERVICE_BINDING_PROTOCOL*This,
  IN OUT EFI_HANDLE*ChildHandle
);
EFI_STATUS
(EFIAPI *EFI_SERVICE_BINDING_DESTROY_CHILD) (
  IN EFI_SERVICE_BINDING_PROTOCOL*This,
  IN EFI_HANDLEChildHandle
);

```
</pre></div>

Note:


---
@title[UEFI Service Binding Protocol Functions]
<p align="center"><span class="gold" ><b>UEFI Service Binding Protocol</b></span></p>
<br>
<ul>
  <li><span style="font-size:0.9em" >`CreateChild()`</span></li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Synchronous hot-plug  add event</span></li>
  </ul>
  <li><span style="font-size:0.9em" >`DestroyChild()`</span></li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Synchronous hot-plug  remove event</span></li>
  </ul>
  <li><span style="font-size:0.9em" >Consumers</span></li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Test for UEFI Service Binding Protocols for the software services the consumer depends upon</span></li>
    <li><span style="font-size:0.7em" >Call `CreateChild()` from `Start()` for each dependent software service</span></li>
    <li><span style="font-size:0.7em" >Creates a child handle with one or more software services</span></li>
    <li><span style="font-size:0.7em" >Call `DestroyChild()` from Stop() for each dependent software service </span></li>
  </ul>
</ul> 

Note:




---?image=/assets/images/slides/Slide111.JPG
<!-- .slide: data-transition="none" -->
@title[NO Interrupts ]

<p align="right"><span class="gold" ><b>EDK II Only Supports Polling (NO Interrupts)</b></span></p>

Note:

+++?image=/assets/images/slides/Slide112.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[NO Interrupts 02]
<p align="right"><span class="gold" ><b>EDK II Only Supports Polling (NO Interrupts)</b></span></p>
<br>
<ul>
  <li><span style="font-size:0.8em" >The IO engine of the whole software stack – POLLING, either timer driven or invoked in applications. </span></li>
  <li><span style="font-size:0.8em" ><b>Asynchronous</b> – data transmission is divided   into two part, similar with the asynchronous IO in OS scope:    1. initiate the IO via a <b>request</b>;   2. wait for the result of the IO request through <b>event</b> notification.  </span></li>
  <li><span style="font-size:0.8em" >Most drivers support data block scatter/gather during transmission. </span></li>
  <li><span style="font-size:0.8em" >Separated IP, Route configurations for each instances based on IP, UDP, TCP, MTFTP and DHCP (Both IPv4 and IPv6) </span></li>
  <li><span style="font-size:0.8em" >Instances are bound to a NIC on creation. No sharing mechanism in layers spanning over multiple NICs. </span></li>
</ul>

Note:

1. The EDK II doesn’t support interrupt handling.


---?image=/assets/images/slides/Slide114.JPG
<!-- .slide: data-transition="none" -->
@title[Deferred Procedure Call Protocol (DPC) ]
<p align="center"><span class="gold" ><b>Deferred Procedure Call Protocol (DPC)</b></span></p>

Note:

+++?image=/assets/images/slides/Slide115.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Deferred Procedure Call Protocol (DPC) 02 ]
<p align="center"><span class="gold" ><b>Deferred Procedure Call Protocol (DPC)</b></span></p>

Note:



---
@title[EDK II DPC Protocol code]
<br>
<p align="center"><span class="gold" ><b>EDK II DPC Protocol</b></span></p>
<br>
<span style="font-size:0.9em" >Code Example</span>
<br>

<div class="left">
<span style="font-size:0.9em" >Queue DPC</span>
<pre>
```
typtypedef
EFI_STATUS
(EFIAPI *EFI_DPC_QUEUE_DPC)(
  IN EFI_DPC_PROTOCOL   *This,
  IN EFI_TPL            DpcTpl,
  IN EFI_DPC_PROCEDURE  DpcProcedure,
  IN VOID               *DpcContext    OPTIONAL
  );

```
</pre>
</div>
<div class="right1">
<span style="font-size:0.9em" >Dispatch DPC</span>
<pre>
```
typedef
EFI_STATUS
(EFIAPI *EFI_DPC_DISPATCH_DPC)(
  IN EFI_DPC_PROTOCOL  *This
  );

```
</pre>
</div>

Note:

- The DPC protocol only has 2 interfaces: QueueDpc() and DispatchDpc().

- The function QueueDpc() queues the DPC Procedure specified by DpcProcedure to be execute at a later time when the TPL level is at or below the TPL level specified by DpcTpl. When DpcProcedureis invoked, the one parameter specified by DpcContext is passed to DpcProcedure. This function is required to maintain a unique queue for every legal EFI_TPL value. The DPC Procedure specified by DpcProcedure and DpcContext is placed at the end of the DPC queue specified by DpcTpl.
- The DPC driver does not take the responsibility to invoke the queued DPCs. Instead, the UEFI driver or application which calls QueueDpc() is responsible for calling DispatchDpc() to dispatch them from lower TPL levels at an appropriate time.

- The function DispatchDpc() dispatches all the previously queued DPCs whose TPL level is greater than or equal to the current TPL level. DPCs with the highest TPL level are dispatched before DPCs with lower TPL levels. Within a single TPL level, the DPCs are dispatched in the order that they were queued by QueueDpc().




---?image=/assets/images/slides/Slide118.JPG
<!-- .slide: data-transition="none" -->
@title[WHY DPC]
### <p align="center"><span class="gold" ><b>Why DPC?</b></span></p>

Note:
- The DPC protocol is designed to solve the TPL issue in UEFI network stack
- Take the iSCSI for example, the UEFI SCSI stack lays on top of the TCP network stack, as shown 

- The network stack from MNP to TCP is asynchronous, that is, all data transmitting and receiving are conveyed by tokens. Each token has an event which associates with a notify function. When the transmitting or receiving is done, the event is signaled with the corresponding I/O status and optionally the data buffer.
- The SCSI stack and block I/O drivers can be asynchronous or synchronous from UEFI Specification, we only discuss the synchronous situation here.

- The UEFI iSCSI driver provides the linkage between the asynchronous network stack and the synchronous SCSI stack. The UEFI iSCSI driver is implemented using a synchronous solution, to avoid the performance hit by polling the network cards in periodical timers for receiving frames.


- TPL issue in iSCSI  ( Deadlock issue)
- UEFI Specification states that all UEFI network stack protocols and their service binding protocols should be called with TPL <= TPL_CALLBACK (see Table 24. TPL Restrictions in UEFI Specification v2.6).
- Above TPL restrictions, plus the asynchronous interfaces and some specific nature of network, make the UEFI network stack driver can only lock itself at TPL_CALLBACK. Take the ARP driver for example. Usually it will response the received ARP requests with ARP replies. The TPL of notify function to parse the received ARP requests should be >= TPL_CALLBACK because it need to access shared structures in ARP driver. When the ARP request is parsed and an ARP reply should be sent out, Mnp->Transmit() would be called to transmit the ARP reply. The TPL for calling the Mnp->Transmit() should be <= TPL_CALLBACK according to the TPL restrictions defined in the UEFI specification. As a result, these two restrictions make the ARP driver can only run at TPL_CALLBACK.
- UEFI Specification also states the Simple File System protocol should be called with TPL <= TPL_CALLBACK. Take FAT driver as the example, it will lock itself at TPL_CALLBACK when accessing the shared structures, or in critical section such as reading block, writing block, etc.
- Now the problem comes out: once the Simple File System driver is controlling the iSCSI stack, and attempting to read a block, iSCSI can NOT receive data from network stack any more. Actually, the data could be received into the buffer pool in MNP driver when iSCSI is polling the network. However, as all the tokens of the upper network stack drivers are created with TPL_CALLBACK, the notify function won't have the chance to run even though the receive event is already signaled. In the other words, the synchronous data read function in iSCSI driver will continue polling the network device at TPL_CALLBACK, and waiting the receive event's notify function, which is also a TPL_CALLBACK event, to be execute first. 

- As a result, the whole iSCSI stack falls into a deadlock, no packet could be delivered to the upper layer drivers.


+++?image=/assets/images/slides/Slide119.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[WHY DPC 02]
### <p align="center"><span class="gold" ><b>Why DPC?</b></span></p>

Note:
#### DPC Solves the TPL deadlock issue in UEFI network stack

- Where no packet could be delivered to the upper layer drivers

- The DPC protocol is designed to solve the TPL issue in UEFI network stack
- Take the iSCSI for example, the UEFI SCSI stack lays on top of the TCP network stack, as shown 

- The network stack from MNP to TCP is asynchronous, that is, all data transmitting and receiving are conveyed by tokens. Each token has an event which associates with a notify function. When the transmitting or receiving is done, the event is signaled with the corresponding I/O status and optionally the data buffer.
- The SCSI stack and block I/O drivers can be asynchronous or synchronous from UEFI Specification, we only discuss the synchronous situation here.

- The UEFI iSCSI driver provides the linkage between the asynchronous network stack and the synchronous SCSI stack. The UEFI iSCSI driver is implemented using a synchronous solution, to avoid the performance hit by polling the network cards in periodical timers for receiving frames.


- TPL issue in iSCSI  ( Deadlock issue)
- UEFI Specification states that all UEFI network stack protocols and their service binding protocols should be called with TPL <= TPL_CALLBACK (see Table 24. TPL Restrictions in UEFI Specification v2.6).
- Above TPL restrictions, plus the asynchronous interfaces and some specific nature of network, make the UEFI network stack driver can only lock itself at TPL_CALLBACK. Take the ARP driver for example. Usually it will response the received ARP requests with ARP replies. The TPL of notify function to parse the received ARP requests should be >= TPL_CALLBACK because it need to access shared structures in ARP driver. When the ARP request is parsed and an ARP reply should be sent out, Mnp->Transmit() would be called to transmit the ARP reply. The TPL for calling the Mnp->Transmit() should be <= TPL_CALLBACK according to the TPL restrictions defined in the UEFI specification. As a result, these two restrictions make the ARP driver can only run at TPL_CALLBACK.
- UEFI Specification also states the Simple File System protocol should be called with TPL <= TPL_CALLBACK. Take FAT driver as the example, it will lock itself at TPL_CALLBACK when accessing the shared structures, or in critical section such as reading block, writing block, etc.
- Now the problem comes out: once the Simple File System driver is controlling the iSCSI stack, and attempting to read a block, iSCSI can NOT receive data from network stack any more. Actually, the data could be received into the buffer pool in MNP driver when iSCSI is polling the network. However, as all the tokens of the upper network stack drivers are created with TPL_CALLBACK, the notify function won't have the chance to run even though the receive event is already signaled. In the other words, the synchronous data read function in iSCSI driver will continue polling the network device at TPL_CALLBACK, and waiting the receive event's notify function, which is also a TPL_CALLBACK event, to be execute first. 

- As a result, the whole iSCSI stack falls into a deadlock, no packet could be delivered to the upper layer drivers.


---?image=/assets/images/slides/Slide122.JPG
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem ]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem </b></span></p>

Note:
- How DPC solve the problem
- The edk2 network stack solves this deadlock problem by introducing the DPC protocol. Whenever a driver wants to call the asynchronous transmit or receive function, it creates an event with TPL_NOTIFY instead of TPL_CALLBACK. The notify function won't really process the packet, it only queues a new DPC Procedure and return. Later, the DPC Procedure will be dispatched at TPL_CALLBACK, and complete the whole task of the packet processing. With this technique, the deadlock is avoided by using a high level TPL event, and the packets are still processed in the required TPL_CALLBACK level.


+++?image=/assets/images/slides/Slide123.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem 02]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem </b></span></p>

Note:
- How DPC solve the problem
- The edk2 network stack solves this deadlock problem by introducing the DPC protocol. Whenever a driver wants to call the asynchronous transmit or receive function, it creates an event with TPL_NOTIFY instead of TPL_CALLBACK. The notify function won't really process the packet, it only queues a new DPC Procedure and return. Later, the DPC Procedure will be dispatched at TPL_CALLBACK, and complete the whole task of the packet processing. With this technique, the deadlock is avoided by using a high level TPL event, and the packets are still processed in the required TPL_CALLBACK level.


+++?image=/assets/images/slides/Slide124.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem 03]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem </b></span></p>

Note:
- How DPC solve the problem
- The edk2 network stack solves this deadlock problem by introducing the DPC protocol. Whenever a driver wants to call the asynchronous transmit or receive function, it creates an event with TPL_NOTIFY instead of TPL_CALLBACK. The notify function won't really process the packet, it only queues a new DPC Procedure and return. Later, the DPC Procedure will be dispatched at TPL_CALLBACK, and complete the whole task of the packet processing. With this technique, the deadlock is avoided by using a high level TPL event, and the packets are still processed in the required TPL_CALLBACK level.



---?image=/assets/images/slides/Slide126.JPG
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.


+++?image=/assets/images/slides/Slide127.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 02]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.


+++?image=/assets/images/slides/Slide128.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 03]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.

+++?image=/assets/images/slides/Slide129.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 04]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.

+++?image=/assets/images/slides/Slide130.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 05]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.

+++?image=/assets/images/slides/Slide131.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 06]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.

+++?image=/assets/images/slides/Slide132.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 07]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.

+++?image=/assets/images/slides/Slide133.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[How DPC Solves the Problem -ARP 08]
<p align="center"><span class="gold" ><b>How DPC Solves the Problem - ARP</b></span></p>

Note:
- How DPC solve the problem
- ARP Example:

- The ARP driver creates an event as the MNP receive token, whose notify function is ArpOnFrameRcvd() and notify TPL set to TPL_NOTIFY. When the Mnp->Poll() receives a new packet and signals this receive event, the ArpOnFrameRcvd() will execute immediately (because it's a TPL_NOTIFY event, which could interrupt any network task whose TPL <= TPL_CALLBACK). The ArpOnFrameRcvd() calls QueueDpc() to queue a new DPC Procedure ArpOnFrameRcvdDpc() at TPL_CALLBACK and return. Later, the Mnp->Poll() calls the DispatchDpc(), to dispatch the DPC Procedure queued by the notify function of the receive token's event, which finally executes the ArpOnFrameRcvdDpc() in this case.



---?image=/assets/images/slides/Slide135.JPG
@title[UEFI Managed Network Protocol (MNP) ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:
- MNP provides for multiple listeners and also provides a non-blocking interface, unlike the single consumer, blocking nature of SNP and UNDI.  We took the concept of multiple consumers and non-blocking for the higher layer protocols, including UDP, TFTP, DHCP, and TCP/IP.

- We took the concept of multiple consumers and non-blocking for the higher layer protocols, including UDP, TFTP, DHCP, and TCP/IP.   In doing so, we were able to rewrite the PXE BC application to be a small consumer of the below-listed services versus the monolithic stack embedded in the original PXE BC. 

- Same Network Device
- The services that are provided by MNP child drivers make it possible for multiple drivers and applications to send and receive network traffic using the same network device. 




---?image=/assets/images/slides/Slide137.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI MNP ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:


+++?image=/assets/images/slides/Slide138.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI MNP 02 ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:
#### Transmission:
- Transmitting packets is simple in the MNP driver -  if MNP just appends the media header to the packets and send it via SNP regardless of the return status of the SNP sending function. 


+++?image=/assets/images/slides/Slide139.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI MNP 03 ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:

#### Receiving:
- Fetch  - a buffer unit from the buffer pool, call SNP.Receive() to receive packets from SNP.
- Delivery -Try to deliver the packet to the appropriate receivers.
- Iterate  - the MNP children, and check the receiving filters of the children against the packet. If matched and there is a receive token submitted by the upper layer protocol, wrap the received packet, queue it into the delivered queue, fill the receive token and signal the event in the token to notify the upper layer protocol.
- Post - Post receiving: recycle the buffer when the recycle event is signaled by the upper layer protocol.


+++?image=/assets/images/slides/Slide140.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI MNP 04 ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:

#### System Polling:
- Use a timer event to periodically poll the SNP driver 
- Guarantee in-sequence packets delivery. 
- Intelligent Poll


+++?image=/assets/images/slides/Slide141.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI MNP 05 ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:

#### Buffer management
- The MNP driver needs pre-allocation of enough buffer units for receiving to reduce the overhead.


+++?image=/assets/images/slides/Slide142.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI MNP 06 ]
<p align="right"><span class="gold" ><b>UEFI Managed Network Protocol (MNP) </b></span></p>

Note:
#### Transmission:
- Transmitting packets is simple in the MNP driver -  if MNP just appends the media header to the packets and send it via SNP regardless of the return status of the SNP sending function. 

#### Receiving:
- Fetch  - a buffer unit from the buffer pool, call SNP.Receive() to receive packets from SNP.
- Delivery -Try to deliver the packet to the appropriate receivers.
- Iterate  - the MNP children, and check the receiving filters of the children against the packet. If matched and there is a receive token submitted by the upper layer protocol, wrap the received packet, queue it into the delivered queue, fill the receive token and signal the event in the token to notify the upper layer protocol.
- Post - Post receiving: recycle the buffer when the recycle event is signaled by the upper layer protocol.

#### System Polling:
- Use a timer event to periodically poll the SNP driver 
- Guarantee in-sequence packets delivery. 
- Intelligent Poll

#### Buffer management
- The MNP driver needs pre-allocation of enough buffer units for receiving to reduce the overhead.


---  
@title[IPv4 Driver – in Detail]
<br>
<p align="center"<span class="gold"   >IPv4 Driver – in Detail </span></p>
<br>
<span style="font-size:0.8em" >Source &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description</span>
```
 Ip4Common.c     Common helper routines for the whole driver  
 
 Ip4Driver.c     DriverBinding and ServiceBinding routines

 Ip4Icmp.c       Internet Control Message Protocol ICMP related routines

 Ip4If.c         IP pseudo interface related routines

 Ip4Igmp.c       Internet Group Management Protocol IGMP related routines 

 Ip4Impl.c       Codes for the APIs defined and exposed by EFI_IP4_PROTOCOL 

 Ip4Input.c      IP packets input (receive) procedure

 Ip4Output.c     IP packets output (transmit) procedure  

 Ip4Route.c      Route table related routines

```

Note:


 
 
---  
@title[IPv6 Driver – in Detail]
<br>
<p align="center"<span class="gold"   >IPv6 Driver – in Detail </span></p>
<br>
<span style="font-size:0.8em" >Source &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description</span>
```
 Ip6Common.c     Common helper routines for the whole driver   

 Ip6Driver.c     DriverBinding and ServiceBinding routines

 Ip6Icmp.c       Internet Control Message Protocol ICMP related routines

 Ip6If.c         IP pseudo interface related routines
//   Different from IPv4   
 Ip6Nd.c         Neighbor Discovery ND related routines

 Ip6Mld.c        Multicast Listener Discovery MLD related routines
//
 Ip6Impl.c       Codes for the APIs defined and exposed by EFI_Ip6_PROTOCOL 

 Ip6Input.c      IP packets input (receive) procedure

 Ip6Output.c     IP packets output (transmit) procedure  

 Ip6Route.c      Route table related routines

```
Note:


---?image=/assets/images/slides/Slide146.JPG
<!-- .slide: data-transition="none" -->
@title[IP Internal Structure – Example IPv4 ]
<p align="right"><span class="gold" ><b>IP Internal Structure – Example IPv4 </b></span></p>

Note:
- In this case, there are 3 IP4 interfaces differed by the Ip/SubnetMask pair.

1. First of all, we always have the default interface with the Ip/SubnetMask originated from the EFI_IP4_CONFIG2_PROTOCOL. We also have two IP4 interfaces manually configured on the creation of an IP4_PROTOCOL instance with manual address configuration, 192.168.1.10/24, 192.168.23.198/24. The IP4_SERVICE and IP4_INTERFACE are associated by IP4_SERVICE.Interfaces and IP4_INTERFACE.Link which in turn form a double-linked list.

2. Each of the two IP4 interfaces has two IP4_PROTOCOL instances associated with. The IP4 interfaces aggregates the IP4_PROTOCOL instances by IP4_INTERFACE.IpInstances and the respective IP4_PROTOCOL.AddrLink to from a double-linked list.

3. All IP4_PROTOCOL instances are associated with the IP4_SERVICE by link IP4_PROTOCOL.Link to IP4_SERVICE.Children to form another double-linked list. Also, the number of IP4_PROTOCOL instances are kept in IP4_SERVICE.NumChildren.

+++?image=/assets/images/slides/Slide147.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IP Internal Structure – Example IPv4 02 ]
<p align="right"><span class="gold" ><b>IP Internal Structure – Example IPv4 </b></span></p>

Note:
- In this case, there are 3 IP4 interfaces differed by the Ip/SubnetMask pair.

1. First of all, we always have the default interface with the Ip/SubnetMask originated from the EFI_IP4_CONFIG2_PROTOCOL. We also have two IP4 interfaces manually configured on the creation of an IP4_PROTOCOL instance with manual address configuration, 192.168.1.10/24, 192.168.23.198/24. The IP4_SERVICE and IP4_INTERFACE are associated by IP4_SERVICE.Interfaces and IP4_INTERFACE.Link which in turn form a double-linked list.

2. Each of the two IP4 interfaces has two IP4_PROTOCOL instances associated with. The IP4 interfaces aggregates the IP4_PROTOCOL instances by IP4_INTERFACE.IpInstances and the respective IP4_PROTOCOL.AddrLink to from a double-linked list.

3. All IP4_PROTOCOL instances are associated with the IP4_SERVICE by link IP4_PROTOCOL.Link to IP4_SERVICE.Children to form another double-linked list. Also, the number of IP4_PROTOCOL instances are kept in IP4_SERVICE.NumChildren.

+++?image=/assets/images/slides/Slide148.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IP Internal Structure – Example IPv4 03 ]
<p align="right"><span class="gold" ><b>IP Internal Structure – Example IPv4 </b></span></p>

Note:
- In this case, there are 3 IP4 interfaces differed by the Ip/SubnetMask pair.

1. First of all, we always have the default interface with the Ip/SubnetMask originated from the EFI_IP4_CONFIG2_PROTOCOL. We also have two IP4 interfaces manually configured on the creation of an IP4_PROTOCOL instance with manual address configuration, 192.168.1.10/24, 192.168.23.198/24. The IP4_SERVICE and IP4_INTERFACE are associated by IP4_SERVICE.Interfaces and IP4_INTERFACE.Link which in turn form a double-linked list.

2. Each of the two IP4 interfaces has two IP4_PROTOCOL instances associated with. The IP4 interfaces aggregates the IP4_PROTOCOL instances by IP4_INTERFACE.IpInstances and the respective IP4_PROTOCOL.AddrLink to from a double-linked list.

3. All IP4_PROTOCOL instances are associated with the IP4_SERVICE by link IP4_PROTOCOL.Link to IP4_SERVICE.Children to form another double-linked list. Also, the number of IP4_PROTOCOL instances are kept in IP4_SERVICE.NumChildren.

---?image=/assets/images/slides/Slide150.JPG
<!-- .slide: data-transition="none" -->
@title[IP4/6 Input Workflow ]
<p align="right"><span class="gold" ><b>IP4/6 Input Workflow</b></span></p>

Note:
- Ip4ReceiveFrame ()
  - Request to receive the packet from the interface. Wrap receive procedure related information into an IP4_LINK_RX_TOKEN. On completion of the receive, Ip4OnFrameReceived () and Ip4OnFrameReceivedDpc (). After some simple check is done, the CallBack function provided will be called with a packet, or some error information. Normally, the CallBack function is Ip4AcceptFrame ().

- Ip4AcceptFrame ()
  - Most work of processing a received IP packet is done here.
  - Sanity check: version number, checksum, size, options, etc.
  - Reassemble fragments of an big IP packet.
  - Invoke IGMP or ICMP processing if it’s an IGMP or ICMP packet respectively, else invoke Ip4Demultiplex () to demultiplex the packet to any IP4 instance who is interested in it.
  - the receive procedure by calling Ip4ReceiveFrame ().
- Ip4Demultiplex ()
  - Iterate all the Ip4 Interfaces, and calling Ip4InterfaceEnquePacket () to let every Ip4 Interface check whether this IP4 packet matches their receive filter. If matches, enqueue it; else, do nothing.
  - If any IP4 interface is willing to receive this packet, iterate all the IP4 interfaces and call Ip4InterfaceDeliverPacket ().

- Ip4InterfaceEnquePacket ()
  - Match cast type first, such as, Multicast, Broadcast or Promiscuous.
  - Iterate all the Ip4 instances belonging to this Interface by calling Ip4InstanceEnquePacket () to check whether there is instance interested in this packet.
- Ip4InterfaceDeliverPacket ()
  - Iterate all the IP4 instances and call Ip4InstanceDeliverPacket () to deliver any queued packets of the instances
- Ip4InstanceEnquePacket ()
  - Check whether this instance is willing to receive the current IP packet. If all match rules are passed, clone this packet and put it into the Received list.
- Ip4InstanceDeliverPacket ()
  - Deliver all the queued IP packets to the consumer of this IP4 protocol by every time putting an IP packet into a consumer provided EFI_IP4_COMPETION_TOKEN, and finally signal the event in the token. The end condition is either there is no IP packet or no consumer provided token.
  - The consumer provided tokens for receive purpose come from the callings to EFI_IP4_PROTOCOL.Receive ().

+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IP4/6 Input Workflow DETAILs]
<br>
<p align="right"><span class="gold" ><b>IP4/6 Input Workflow - Details</b></span></p>
<div class="left">
<pre>
```
Ip4ReceiveFrame ()
  - Request to receive the packet from the interface. Wrap receive 
    procedure related information into an IP4_LINK_RX_TOKEN. On 
	completion of the receive, Ip4OnFrameReceived () and 
	Ip4OnFrameReceivedDpc (). After some simple check is done, the 
	CallBack function provided will be called with a packet, or some error 
    information. Normally, the CallBack function is Ip4AcceptFrame ().
Ip4AcceptFrame ()
  - Most work of processing a received IP packet is done here.
   - Sanity check: version number, checksum, size, options, etc.
   - Reassemble fragments of an big IP packet.
   - Invoke IGMP or ICMP processing if it’s an IGMP or ICMP packet 
     respectively, else invoke Ip4Demultiplex () to demultiplex the 
	 packet to any IP4 instance who is interested in it.
 - the receive procedure by calling Ip4ReceiveFrame ().
Ip4Demultiplex ()
  - Iterate all the Ip4 Interfaces, and calling Ip4InterfaceEnquePacket () 
    to let every Ip4 Interface check whether 
    this IP4 packet matches their receive filter. If matches, enqueue it; 
	else, do nothing.
  - If any IP4 interface is willing to receive this packet, iterate all 
    the IP4 interfaces and call Ip4InterfaceDeliverPacket ().
```
</pre>
</div>
<div class="right1">
<pre>
```
Ip4InterfaceEnquePacket ()
- Match cast type first, such as, Multicast, Broadcast or Promiscuous.
- Iterate all the Ip4 instances belonging to this Interface by calling 
  Ip4InstanceEnquePacket () to check whether there is instance 
  interested in this packet.
Ip4InterfaceDeliverPacket ()
- Iterate all the IP4 instances and call Ip4InstanceDeliverPacket () 
  to deliver any queued packets of the instances
Ip4InstanceEnquePacket ()
- Check whether this instance is willing to receive the current 
  IP packet. If all match rules are passed, clone this packet 
  and put it into the Received list.
Ip4InstanceDeliverPacket ()
- Deliver all the queued IP packets to the consumer of this IP4 
  protocol by every time putting an IP packet into a consumer provided 
  EFI_IP4_COMPETION_TOKEN, and finally signal the event in the token. 
  The end condition is either there is no IP packet or no consumer 
  provided token.
- The consumer provided tokens for receive purpose come from the 
  callings to EFI_IP4_PROTOCOL.Receive ().
```
</pre>
</div>

Note:


---?image=/assets/images/slides/Slide153.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IP4/6 Output Workflow ]
<p align="right"><span class="gold" ><b>IP4/6 Output Workflow</b></span></p>

Note:

- EfiIp4/6Transmit () – EFI_IP4/6_PROTOCOL.Transmit ()
  - The initial source of most IP4/6 output packets.
  - Sanity check.
  - Append IP4/6 head to the buffer passed in.
  - Record the Token and the corresponding Wrap (IP4/6_TXTOKEN_WRAP)  
    to the TxTokens NET_MAP.
  - Call Ip4/6Output to output this packet.
- Ip4/6Output ()
  - Decide the IP address of the next hop for this packet, aka, route selection.
  - Fragment it if needed.
  - Call Ip4/6SendFrame () to send this packet.

- Ip4/6SendFrame ()
  - Do layer-3 to layer-2 address translation, in most cases need the help from the Arp instance belonging to the IP4 interface selected.
  - Immediately send out the packet by Mnp->Transmit if the translation can be done directly from the arp cache.  
  - Or create an ArpQue which assembles all the IP4 packets with the same next hop. Once the translation is done, all these packets are transmitted out in the event notify function.
  - Upon completion of the transmit, either successful or with some failure, the status will be returned to the consumer provided EFI_IP4/6_COMPLETION_TOKEN.Status with the signaling of the event, and at this time, the control of the token is returned to the consumer.



+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[IP4/6 Output Workflow DETAILs]
<p align="right"><span class="gold" ><b>IP4/6 Output Workflow - Details</b></span></p>
<br>
<div class="left">
<pre>
```
EfiIp4/6Transmit () – EFI_IP4/6_PROTOCOL.Transmit ()
  - The initial source of most IP4/6 output packets.
  - Sanity check.
  - Append IP4/6 head to the buffer passed in.
  - Record the Token and the corresponding Wrap 
    (IP4/6_TXTOKEN_WRAP)  to the TxTokens NET_MAP.
  - Call Ip4/6Output to output this packet.
Ip4/6Output ()
  - Decide the IP address of the next hop for this 
    packet, aka, route selection.
  - Fragment it if needed.
  - Call Ip4/6SendFrame () to send this packet.

```
</pre>
</div>
<div class="right1">
<pre>
```
Ip4/6SendFrame ()
  - Do layer-3 to layer-2 address translation, in most cases 
    need the help from the Arp instance belonging to the IP4 
    interface selected.
     - Immediately send out the packet by Mnp->Transmit if the 
	   translation can be done directly from the arp cache.  
     - Or create an ArpQue which assembles all the IP4 packets with 
	   the same next hop. Once the translation is done, all these 
	   packets are transmitted out in the event notify function.
Upon completion of the transmit, either successful or with some 
failure, the status will be returned to the consumer provided 
EFI_IP4/6_COMPLETION_TOKEN.Status with the signaling of the event, 
and at this time, the control of the token is returned to the consumer.
```
</pre>
</div>

Note:

---?image=assets/images/binary-strings-black2.jpg
@title[UEFI HTTP(s) Boot Overview Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI HTTP(s) Boot Overview </span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>

Note:

---
@title[UEFI HTTP(s) Boot Overview]
<br>
<p align="right"><span class="gold" ><b>UEFI HTTP(s) Boot Overview</b></span></p>
<span style="font-size:0.9em"> <b>HTTP protocol for network booting</b> </span>
<ul>
  <li><span style="font-size:0.8em">HTTP can handle much larger files than TFTP, and scale to much larger distances. You can easily download multi-megabyte files, such as a Linux kernel and a root file system, and you can download from servers that are not on your local area network</span></li>
  <li><span style="font-size:0.8em">Booting from HTTP is as simple as replacing the DHCP filename field with an http:// URL </span></li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em"> Specify URI <span style="vertical-align: super">1</span>-based pointers to the “Network Boot Program (NBP)”, the binary image to download and run, which can be used using HTTP instead of TFTP</span></li>
  </ul>
  <li><span style="font-size:0.8em">DHCP Servers will need to support  HTTP Boot  </span></li>
</ul>


Note:

- Uniform Resource Identifiers (URI) 
- Uniform Resource Locator(URL)

- A URI can be further classified as a locator, a name, or both. The term "Uniform Resource Locator" (URL) refers to the subset of URIs that, in addition to identifying a resource, provide a means of locating the resource by describing its primary access mechanism (e.g., its network "location").

#### URI
- A URI identifies a resource either by location, or a name, or both. More often than not, most of us use URIs that defines a location to a resource. The fact that a URI can identify a resources by both name and location has lead to a lot of the confusion in my opionion. A URI has two specializations known as URL and URN.

#### URL
- A URL is a specialization of URI that defines the network location of a specific resource. Unlike a URN, the URL defines how the resource can be obtained. We use URLs every day in the form of http://damnhandy.com, etc. But a URL doesn’t have to be an HTTP URL, it can be ftp://damnhandy.com, smb://damnhandy.com, etc.
- The Difference Between Them
- So what is the difference between URI and URL? It’s not as clear cut as I would like, but here’s my stab at it:
- A URI is an identifier for some resource, but a URL gives you specific information as to obtain that resource. A URI is a URL and as one commenter pointed out, it is now considered incorrect to use URL when describing applications. Generally, if the URL describes both the location and name of a resource, the term to use is URI. Since this is generally the case most of us encounter everyday, URI is the correct term.

- https://damnhandy.com/2007/11/19/uri-vs-url-whats-the-difference/
- http://etherboot.org/wiki/httpboot
- https://firmwaresecurity.com/tag/uefi-http-boot/



---?image=/assets/images/slides/Slide158.JPG
@title[HTTP(s) Boot UEFI  Network Stack ]
<p align="center"><span class="gold" ><b>HTTP(s) Boot UEFI Network Stack</b></span></p>
<br>
<div class="left">
<ul>
  <li><span style="font-size:0.8em">DNS IPv4 / IPv6</span></li>
  <li><span style="font-size:0.8em">HTTP IPv4 / IPv6</span></li>
  <li><span style="font-size:0.8em">TLS for HTTPs</span></li>
  <li><span style="font-size:0.8em">HTTP Boot Driver</span></li>
</ul>

</div>
<div class="right1">
<span style="font-size:0.9em">&nbsp;</span>
</div>


Note:

- UEFI Spec 2.6 Fig 72. Sect.: 23.7.3 
- This figure illustrates the UEFI network layers related to how the HTTP Boot works. 
- The HTTP Boot driver is layered on top of a UEFI Network stack implementation. 
- It consumes DHCP service to do the Boot service discovery, and DNS service to do domain name resolution if needed. It also consumes HTTP serviced to retrieve images from the HTTP server. 
- The functionality needed in the HTTP Boot scenario is limited to client initiated requests to download the boot image. TLS is consumed if HTTP(S) functionality is needed 
- The HTTP Boot driver produces LoadFile protocol and device path protocol. 
- BDS will provide the boot options for the HTTP Boot. Once a boot option for HTTP boot is executed, a particular network interface is selected. HTTP Boot driver will perform all steps on that interface and it is not required to use other interfaces. 

- Network stack in UEFI 2.4
  - Ipv4 and Ipv6 – iSCSI
  - Isec

- What  was missing in 2.4
  - Suppport for HTTP boot
  - DNS
  - HTTP boot
  - TLS

- Also added WiFi and  bluetooth  UEFI 2.6



---?image=/assets/images/slides/Slide160.JPG
@title[HTTP(s) Boot UEFI  Network Stack -protocols]
<p align="center"><span class="gold" ><b>HTTP(s) Boot UEFI Network Stack</b></span></p>
<span style="font-size:0.9em">- UEFI & EDK II Protocols</span>
<div class="left">
<pre>
```
- HTTP support
  - EFI_HTTP_SERVICE_BINDING_PROTOCOL
  - EFI_HTTP_PROTOCOL
  - EFI_HTTP_UTILITIES_PROTOCOL
- DNS Support
  - EFI_DNS4_SERVICE_BINDING_PROTOCOL
  - EFI_DNS6_SERVICE_BINDING_PROTOCOL
  - EFI_DNS4_PROTOCOL 
  - EFI_DNS6_PROTOCOL
  - EFI_IP4_CONFIG2_PROTOCOL
  - EFI_IP6_CONFIG_PROTOCOL
- TLS support
  - EFI_TLS_SERVICE_BINDING_PROTOCOL
  - EFI_TLS_PROTOCOL
  - EFI_TLS_CONFIGURATION_PROTOCOL
```
</pre>
</div>
<div class="right">
<span style="font-size:0.9em">&nbsp;</span>
</div>

Note:


---?image=/assets/images/slides/Slide162.JPG
@title[UEFI Native HTTP Boot – Corporate ]
<p align="center"><span class="gold" ><b>UEFI Native HTTP Boot</b></span><span style="font-size:0.8em"><br>- Corporate Environment</span></p>

Note:
- The figure shows:a typical HTTP Boot network topology for a corporate environment 
- Where A typical network configuration supports UEFI HTTP Boot may involve one or more UEFI client systems, and/or several server systems 

 -  UEFI HTTP Boot Client initiates the communication between the client and different server system. 
 -  DHCP server with HTTP Boot extension for boot service discovery. Besides the standard host configuration information (such as address/subnet/gateway/name-server, etc…), the DHCP server with the extensions can also provide the discovery of URI locations for boot images on the HTTP server. 
 -  HTTP server could be located either inside the corporate environment or across networks, such as on the Internet. The boot resource itself is deployed on the HTTP server. In this example, “http://webserver/boot/boot.efi” is used as the boot resource. Such an application is also called a Network Boot Program (NBP). NBPs are used to setup the client system, which may include installation of an operating system, or running a service OS for maintenance and recovery tasks. 
 -  DNS server is optional; and provides standard domain name resolution service. 

- Dynamic Host Configuration Protocol (DHCP) is a client/server protocol that automatically provides an Internet Protocol (IP) host with its IP address and other related configuration information such as the subnet mask and default gateway.


---?image=/assets/images/slides/Slide164.JPG
@title[HTTP Boot DHCP Discovery ]
<p align="center"><span class="gold" ><b>HTTP Boot DHCP Discovery</b></span></p>

Note:

- Dynamic Host Configuration Protocol (DHCP) is a client/server protocol that automatically provides an Internet Protocol (IP) host with its IP address and other related configuration information such as the subnet mask and default gateway.

- The Dynamic Host Configuration Protocol (DHCP) is a standardized network protocol used on Internet Protocol (IP) networks for dynamically distributing network configuration parameters, such as IP addresses for interfaces and services.

- The DHCP employs a connectionless service model, using the User Datagram Protocol (UDP). It is implemented with two UDP port numbers for its operations which are the same as for the BOOTP protocol. UDP port number 67 is the destination port of a server, and UDP port number 68 is used by the client.


+++?image=/assets/images/slides/Slide165.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP Boot DHCP Discovery 02]
<p align="center"><span class="gold" ><b>HTTP Boot DHCP Discovery</b></span></p>

Note:

- Dynamic Host Configuration Protocol (DHCP) is a client/server protocol that automatically provides an Internet Protocol (IP) host with its IP address and other related configuration information such as the subnet mask and default gateway.

- The Dynamic Host Configuration Protocol (DHCP) is a standardized network protocol used on Internet Protocol (IP) networks for dynamically distributing network configuration parameters, such as IP addresses for interfaces and services.

- The DHCP employs a connectionless service model, using the User Datagram Protocol (UDP). It is implemented with two UDP port numbers for its operations which are the same as for the BOOTP protocol. UDP port number 67 is the destination port of a server, and UDP port number 68 is used by the client.



+++?image=/assets/images/slides/Slide166.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP Boot DHCP Discovery 03]
<p align="center"><span class="gold" ><b>HTTP Boot DHCP Discovery</b></span></p>

Note:

- Dynamic Host Configuration Protocol (DHCP) is a client/server protocol that automatically provides an Internet Protocol (IP) host with its IP address and other related configuration information such as the subnet mask and default gateway.

- The Dynamic Host Configuration Protocol (DHCP) is a standardized network protocol used on Internet Protocol (IP) networks for dynamically distributing network configuration parameters, such as IP addresses for interfaces and services.

- The DHCP employs a connectionless service model, using the User Datagram Protocol (UDP). It is implemented with two UDP port numbers for its operations which are the same as for the BOOTP protocol. UDP port number 67 is the destination port of a server, and UDP port number 68 is used by the client.


+++?image=/assets/images/slides/Slide167.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[HTTP Boot DHCP Discovery 04]
<p align="center"><span class="gold" ><b>HTTP Boot DHCP Discovery</b></span></p>

Note:

- Dynamic Host Configuration Protocol (DHCP) is a client/server protocol that automatically provides an Internet Protocol (IP) host with its IP address and other related configuration information such as the subnet mask and default gateway.

- The Dynamic Host Configuration Protocol (DHCP) is a standardized network protocol used on Internet Protocol (IP) networks for dynamically distributing network configuration parameters, such as IP addresses for interfaces and services.

- The DHCP employs a connectionless service model, using the User Datagram Protocol (UDP). It is implemented with two UDP port numbers for its operations which are the same as for the BOOTP protocol. UDP port number 67 is the destination port of a server, and UDP port number 68 is used by the client.




---?image=/assets/images/slides/Slide169.JPG
@title[HTTP(s) Boot Discovery - Architectural Types ]
<p align="right"><span class="gold" ><b>HTTP(s) Boot Discovery - Architectural Types</b></span></p>
<br>
<div class="left1">
<ul>
  <li><span style="font-size:0.8em"> DHCP - <a href="http://www.iana.org/assignments/dhcpv6-parameters/dhcpv6-parameters.xml"> dhcpv6-parameters.xml</a></span> </li>
  <li><span style="font-size:0.8em">IPv4/IPv6 DHCP Discover request </span> </li>
  <ul style="list-style-type:disc">
     <li><span style="font-size:0.7em">DHCP Option 93: Client system Architecture </span> </li>
     <li><span style="font-size:0.7em">DHCPv6 Option 61: Client system Architecture </span> </li>
	 <ul style="list-style-type:none">
	   <li><span style="font-size:0.5em">`0x10 = x64 UEFI boot from HTTP ` </span> </li>
	   <li><span style="font-size:0.5em">`0x0F = x86 UEFI boot from HTTP ` </span> </li>
     </ul>
  </ul>
  <li><span style="font-size:0.8em">Server responds with DHCPOFFER that includes the boot file HTTP URI for the requested processor architecture  </span> </li>
</ul>
</div>
<div class="right1">
<span style="font-size:0.9em">&nbsp;</span>
</div>


Note:

---
@title[iPXE – UEFI HTTP Chainloading ]
<br>
<p align="center"><span class="gold" ><b>iPXE – UEFI HTTP Chainloading</b></span></p>
<br>
<span style="font-size:0.9em">UEFI HTTP Boot client to chainload iPXE from an HTTP server   (HTTP boot to iPXE then run iPXE to HTTP download)</span>
<ul>
 <li><span style="font-size:0.8em">Eliminates need for separate TFTP server</span> </li>
 <li><span style="font-size:0.8em">UEFI HTTP Boot client will download and boot iPXE </span> </li>
 <li><span style="font-size:0.8em">iPxe offers advanced features to download and boot OS </span> </li>
 <li><span style="font-size:0.7em">Application note: <a href="http://ipxe.org/appnote/uefihttp"> ipxe.org/Uefihttp </a>   </span> </li>
</ul>
<p align="center"><span style="font-size:01.0em" >&nbsp;<span style="background-color: #7030a0"><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 Options to address the PXE challenges: &nbsp;&nbsp;&nbsp;&nbsp;<br><br>Native UEFI HTTP Boot  and  iPXE using UEFI HTTP</b> &nbsp;&nbsp;</b></span></p>

Note:

- Adds support of HTTP Boot:
  –Used to only work with traditional BIOS, users have to choose between HTTP Boot and UEFI Secure Boot
  –Used to only provides low-level SNP interface (no HTTP Boot) in UEFI
  –Recently “the iPXEUEFI vision has mostly been implemented”
  –Not part of the UEFI standard

- iPXEUEFI vision
  –“Provide the same advanced features within the UEFI environment as are currently provided within the Traditional BIOS environment” -http://ipxe.org/efi/vision 



---?image=/assets/images/slides/Slide172.JPG
@title[RAM Disk Boot from HTTP ]
<p align="right"><span class="gold" ><b>RAM Disk Boot from HTTP</b></span></p>

Note:
- RAM Disk

- ACPI 6 Non-Volatile Memory Device Support / NFIT  - Firmware Interface Table (NFIT) Allows description for both NVRAM and memory

- Besides the UEFI formatted executable image, the downloaded boot file could also be an archive file (hard disk image) or an ISO image. The file should contain an UEFI-compliant file system and will be mounted as a RAM disk by HTTP Boot driver, to be proceeded in the subsequent boot process.

- on slide:
- UEFI 2.5 defined RAM Disk device path nodes
  - Standard access to a RAM Disk in UEFI
  - Supports Virtual Disk and Virtual CD (ISO image) in persistent or volatile memory
  - Device Path: Type:4 Subtype: 9
- ACPI 6.0 NVDIMM Firmware Interface Table (NFIT)
  - Describe the RAM Disks to the OS
  - Runtime access of the ISO boot image in memory
- Supported Image Types 
  - *.ISO		Virtual CD Image
  - *.img	Virtual Disk Image
  - *.efi		UEFI Executable Image



---?image=/assets/images/slides/Slide174.JPG
@title[UEFI Http Boot Example]
<p align="right"><span class="gold" ><b>UEFI Http Boot Example</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="font-size:0.6em">White paper <a href="https://github.com/tianocore-docs/Docs/raw/master/White_Papers/EDKIIHttpBootGettingStartedGuide_0_8.pdf"> EDK II HTTP Boot Getting Started Guide </a>for a step by step guide </span>

Note:



---?image=/assets/images/slides/Slide176.JPG
@title[EDK II HTTP Boot Configuration]
<p align="right"><span class="gold" ><b>EDK II HTTP Boot Configuration</b></span></p>

Note:

- In the main page of Boot Manager Menu, enter [Device Manager] -\> [Network Device List] -\> Select a NIC device -\> [HTTP Boot Configuration], set the HTTP boot parameters such as the boot option title, IP start version and the URI address
- Save the configuration and back to the main page, enter [Boot Manager] menu  and select the new created boot option to start the HTTP Boot




---?image=/assets/images/slides/Slide178.JPG
@title[UEFI Native HTTP Boot - Home]
<p align="right"><span class="gold" ><b>UEFI Native HTTP Boot - Home Environment</b></span></p>

Note:
- Only a Standard DHCP server is available for host IP configuration assignment
- Boot file URI needs to be entered by user instead of the DHCP HTTPBoot extensions. 
- The EDK II HTTP Boot Driver provides a configuration pages for the boot file URI setup


---
@title[Getting started Guides]
<br>
<p align="center"><span class="gold" ><b>Getting Started Guides</b></span></p>
<span style="font-size:01.1em">HTTP: </span><br>
<span style="font-size:0.8em"><i>Wiki Page</i> <a href="https://github.com/tianocore/tianocore.github.io/wiki/HTTP-Boot">https://github.com/tianocore/tianocore.github.io/wiki/HTTP-Boot </a></span><br>
<span style="font-size:0.8em">PDF<a href="https://github.com/tianocore-docs/Docs/raw/master/White_Papers/EDKIIHttpBootGettingStartedGuide_0_8.pdf"> EDKIIHttpBootGettingStartedGuide_0_8.pdf</a></span>
<br>
<br>
<span style="font-size:01.1em">HTTPS: </span><br>
<span style="font-size:0.8em"><i>Wiki Page</i> <a href="https://www.gitbook.com/book/edk2-docs/getting-started-with-uefi-https-boot-on-edk-ii/details">https://github.com/tianocore/tianocore.github.io/wiki/HTTPs-Boot </a></span><br>
<span style="font-size:0.8em">PDF<a href="https://www.gitbook.com/book/edk2-docs/getting-started-with-uefi-https-boot-on-edk-ii/details"> UEFI HTTPS Boot on EDK II .pdf</a></span>

Note:










---  
@title[Summary]
<BR>
### <p align="center"><span class="gold"   >Summary </span></p><br>
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI  Network Stack Layers<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; host and target basic configuration and components</span> </li>
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;EDK II Network Features Overview </span></li>
 <li>@fa[certificate gp-bullet-gold]<span style="font-size:0.9em">&nbsp;&nbsp;What UEFI Protocols Make Network Work in EDK II </span> </li>
 <li>@fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI HTTP(s) Boot Overview </span></li>
</ul>

Note:

---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2018, Intel Corporation. All rights reserved.
**/

```

