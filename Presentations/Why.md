
@title[Why Platform FW Security is important Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Why?</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Why is Platform Firmware Security Important ?</span>

Note:
  Why.md for UEFI / EDK II Training  Why Platform FW Security is important

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




---?image=/assets/images/slides/Slide4.JPG
<!-- .slide: data-transition="none" -->
@title[Why is Platform Firmware Security Important ?]
<p align="right"><span class="gold" ><b>Why is Platform Firmware  <br>Security Important ?</b></span></p>

Note:

If we think of FW like plumbing
It needs to  standardized to simplify implementation  (Fitting the pieces of pipe together like standardized plumbing PVC Pipe)
Where we have the Hardware,  the Firmware,  and then hand off to the OS

When we look at why firmware security is important, using the analogy of the plumbing pipeline,
If we are were to run water through this imaginary pipe we would want to know that the water source could be trusted
With Security it is important to establish the root of trust and that we can validated that root of trust.
And it needs to be scalable to work across a variety of needs

New Ideas – new features - 
Dog do-do - Protect from outside attacks. Protect from Things not intended to be put into the firmware

Firmware needs to be done correctly from the get -go


+++?image=/assets/images/slides/Slide5.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Why is Platform Firmware Security Important ? 02]
<p align="right"><span class="gold" ><b>Why is Platform Firmware  <br>Security Important ?</b></span></p>



Note:

If we think of FW like plumbing
It needs to  standardized to simplify implementation  (Fitting the pieces of pipe together like standardized plumbing PVC Pipe)
Where we have the Hardware,  the Firmware,  and then hand off to the OS

When we look at why firmware security is important, using the analogy of the plumbing pipeline,
If we are were to run water through this imaginary pipe we would want to know that the water source could be trusted
With Security it is important to establish the root of trust and that we can validated that root of trust.
And it needs to be scalable to work across a variety of needs

New Ideas – new features - 
Dog do-do - Protect from outside attacks. Protect from Things not intended to be put into the firmware

Firmware needs to be done correctly from the get -go



+++?image=/assets/images/slides/Slide6.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Why is Platform Firmware Security Important ? 03]
<p align="right"><span class="gold" ><b>Why is Platform Firmware <br> Security Important ?</b></span></p>



Note:

If we think of FW like plumbing
It needs to  standardized to simplify implementation  (Fitting the pieces of pipe together like standardized plumbing PVC Pipe)
Where we have the Hardware,  the Firmware,  and then hand off to the OS

When we look at why firmware security is important, using the analogy of the plumbing pipeline,
If we are were to run water through this imaginary pipe we would want to know that the water source could be trusted
With Security it is important to establish the root of trust and that we can validated that root of trust.
And it needs to be scalable to work across a variety of needs

New Ideas – new features - 
Dog do-do - Protect from outside attacks. Protect from Things not intended to be put into the firmware

Firmware needs to be done correctly from the get -go



+++?image=/assets/images/slides/Slide7.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Why is Platform Firmware Security Important ? 04]
<p align="right"><span class="gold" ><b>Why is Platform Firmware <br>Security Important ?</b></span></p>



Note:

If we think of FW like plumbing
It needs to  standardized to simplify implementation  (Fitting the pieces of pipe together like standardized plumbing PVC Pipe)
Where we have the Hardware,  the Firmware,  and then hand off to the OS

When we look at why firmware security is important, using the analogy of the plumbing pipeline,
If we are were to run water through this imaginary pipe we would want to know that the water source could be trusted
With Security it is important to establish the root of trust and that we can validated that root of trust.
And it needs to be scalable to work across a variety of needs

New Ideas – new features - 
Dog do-do - Protect from outside attacks. Protect from Things not intended to be put into the firmware

Firmware needs to be done correctly from the get -go





---?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-transition="none" -->
@title[Why???    Security]
<p align="right"><span class="gold" ><b>Why???    Security</b></span></p>

Note:


- Broken Bottle source CC : https://www.1001freedownloads.com/free-clipart/broken-bottle
- Safe http://www.clipartkid.com/images/252/free-to-use-public-domain-miscellaneous-clip-art-page-41-jsgFX2-clipart.png

- Network attacks 
- Take the preboot execution environment and get bios-level access to the hardware from across the network, outside any control of the on-disk operating system. The pxesploit attack, releasing a new metasploit-based comprehensive PXE attack toolkit to deliver any payload reliably to many different operating systems. 

- Code Injection Attacks
- Important when firmware verifies digital signature
- Depends on implementation flaw in a driver 
- E.g. Stack overflow, heap overflow or incorrect signature verification
- Secure Boot prevents running an unknown OS loader



+++?image=/assets/images/slides/Slide10.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->

@title[Why???    Security 02]
<p align="right"><span class="gold" ><b>Why???    Security</b></span></p>

Note:


- Broken Bottle source CC : https://www.1001freedownloads.com/free-clipart/broken-bottle
- Safe http://www.clipartkid.com/images/252/free-to-use-public-domain-miscellaneous-clip-art-page-41-jsgFX2-clipart.png

- Network attacks 
- Take the preboot execution environment and get bios-level access to the hardware from across the network, outside any control of the on-disk operating system. The pxesploit attack, releasing a new metasploit-based comprehensive PXE attack toolkit to deliver any payload reliably to many different operating systems. 

- Code Injection Attacks
- Important when firmware verifies digital signature
- Depends on implementation flaw in a driver 
- E.g. Stack overflow, heap overflow or incorrect signature verification
- Secure Boot prevents running an unknown OS loader




+++?image=/assets/images/slides/Slide11.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->

@title[Why???    Security 03]
<p align="right"><span class="gold" ><b>Why???    Security</b></span></p>

Note:


- Broken Bottle source CC : https://www.1001freedownloads.com/free-clipart/broken-bottle
- Safe http://www.clipartkid.com/images/252/free-to-use-public-domain-miscellaneous-clip-art-page-41-jsgFX2-clipart.png

- Network attacks 
- Take the preboot execution environment and get bios-level access to the hardware from across the network, outside any control of the on-disk operating system. The pxesploit attack, releasing a new metasploit-based comprehensive PXE attack toolkit to deliver any payload reliably to many different operating systems. 

- Code Injection Attacks
- Important when firmware verifies digital signature
- Depends on implementation flaw in a driver 
- E.g. Stack overflow, heap overflow or incorrect signature verification
- Secure Boot prevents running an unknown OS loader



+++?image=/assets/images/slides/Slide12.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->

@title[Why???    Security 04]
<p align="right"><span class="gold" ><b>Why???    Security</b></span></p>

Note:


- Broken Bottle source CC : https://www.1001freedownloads.com/free-clipart/broken-bottle
- Safe http://www.clipartkid.com/images/252/free-to-use-public-domain-miscellaneous-clip-art-page-41-jsgFX2-clipart.png

- Network attacks 
- Take the preboot execution environment and get bios-level access to the hardware from across the network, outside any control of the on-disk operating system. The pxesploit attack, releasing a new metasploit-based comprehensive PXE attack toolkit to deliver any payload reliably to many different operating systems. 

- Code Injection Attacks
- Important when firmware verifies digital signature
- Depends on implementation flaw in a driver 
- E.g. Stack overflow, heap overflow or incorrect signature verification
- Secure Boot prevents running an unknown OS loader



+++?image=/assets/images/slides/Slide13.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->

@title[Why???    Security 05]
<p align="right"><span class="gold" ><b>Why???    Security</b></span></p>

Note:


- Broken Bottle source CC : https://www.1001freedownloads.com/free-clipart/broken-bottle
- Safe http://www.clipartkid.com/images/252/free-to-use-public-domain-miscellaneous-clip-art-page-41-jsgFX2-clipart.png

- Network attacks 
- Take the preboot execution environment and get bios-level access to the hardware from across the network, outside any control of the on-disk operating system. The pxesploit attack, releasing a new metasploit-based comprehensive PXE attack toolkit to deliver any payload reliably to many different operating systems. 

- Code Injection Attacks
- Important when firmware verifies digital signature
- Depends on implementation flaw in a driver 
- E.g. Stack overflow, heap overflow or incorrect signature verification
- Secure Boot prevents running an unknown OS loader


---?image=/assets/images/slides/Slide4_2.JPG
@title[UEFI Boot Flow]
<p align="right"><span class="gold" >@size[01.1em](<b>Firmware is Everywhere</b>) </span></p>
@snap[north-east span-50 ]
<br>
<p style="line-height:50%" >&nbsp;</p>
@box[bg-navy text-white ](<p style="line-height:70%" ><span style="font-size:0.9em; font-weight: bold;" ><br><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
<br>
@snapend

@snap[north-east span-50 fragment]
<br>
<p style="line-height:50%" ><br>&nbsp;</p>
<ul style="list-style-type:disc; line-height:0.7;">
 <li><span style="font-size:0.65em">GBe NIC, WiFi, Bluetooth, WiGig </span></li>
 <li><span style="font-size:0.65em">Baseband (3G, LTE) Modems </span></li>
 <li><span style="font-size:0.65em">Sensor Hubs </span></li>
 <li><span style="font-size:0.65em">NFC, GPS Controllers </span></li>
 <li><span style="font-size:0.65em">HDD/SSD </span></li>
 <li><span style="font-size:0.65em">Keyboard  Embedded Controllers </span></li>
 <li><span style="font-size:0.65em">Battery Gauge </span></li>
 <li><span style="font-size:0.65em">Baseboard Management Controllers (BMC) </span></li>
 <li><span style="font-size:0.65em">Graphics/Video </span></li>
 <li><span style="font-size:0.65em">USB Thumb Drives, keyboards/mice </span></li>
 <li><span style="font-size:0.65em">Chargers, adapters </span></li>
 <li><span style="font-size:0.65em">TPM, security co-processors </span></li>
 <li><span style="font-size:0.65em">Routers, network appliances </span></li>
</ul>
<br>
@snapend

@snap[north-west span-100 fragment]
<br>
<br>
<br>
<br>
<p style="line-height:20%" ><br><br>&nbsp;</p>
<p style="line-height:20%"  align="left">
&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br>
@fa[splotch gp-bullet-red2]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br>
<br>&nbsp;@fa[splotch gp-bullet-red2]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br><br>
&nbsp;&nbsp;@fa[splotch gp-bullet-red2]<br>
</p>
@snapend




@snap[south-west span-45 fragment]
<p align="right">@fa[splotch gp-bullet-red2]</p>
<p style="line-height:20%" ><br>&nbsp;</p>
@snapend

@snap[south-east span-50 fragment]
@box[bg-royal text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:0.8em; font-weight: bold;" >Main system firmware &lpar;BIOS, UEFI firmware, coreboot&rpar;<br>&nbsp;</span></p>)
@snapend

Note:
### BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  GBe - Gigabit Network Interface controller
  NFC   Near Field Communication
  GPS	Global Positioning System
  HDD/SSD Hard Drive - Solid State Drive
  TPM    Trusted Platform Module

Image source: http://www.tweaktown.com/reviews/7497/tyan-s7076-intel-c612-server-motherboard-review/index3.html

+++?image=/assets/images/slides/Slide4_2.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow]
<p align="right"><span class="gold" >@size[01.1em](<b>Firmware is Everywhere</b>) </span></p>



@snap[south-west span-50 ]
<p align="right">@fa[splotch fa-2x gp-bullet-red2]</p>
@snapend

@snap[south-east span-50 ]
@box[bg-royal text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:0.8em; font-weight: bold;" ><br>Main system firmware &lpar;BIOS, UEFI firmware, coreboot&rpar;<br><br>&nbsp;</span></p>)
<br>
<br>
<br>
<br>
<br>
@snapend

Note:
### BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  GBe - Gigabit Network Interface controller
  NFC   Near Field Communication
  GPS	Global Positioning System
  HDD/SSD Hard Drive - Solid State Drive
  TPM    Trusted Platform Module

Image source: http://www.tweaktown.com/reviews/7497/tyan-s7076-intel-c612-server-motherboard-review/index3.html




---

#### blank page

---?image=/assets/images/slides/Slide15.JPG
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module



+++?image=/assets/images/slides/Slide16.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere 02]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module



+++?image=/assets/images/slides/Slide17.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere 03]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module


+++?image=/assets/images/slides/Slide18.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere 04]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module


+++?image=/assets/images/slides/Slide19.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere 05]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module


+++?image=/assets/images/slides/Slide20.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere 06]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module


+++?image=/assets/images/slides/Slide21.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Firmware Everywhere 07]
<p align="right"><span class="gold" ><b>Firmware Everywhere</b></span></p>

Note:

- BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  -   GBe - Gigabit Network Interface controller
  - NFC   Near Field Communication
  -   GPS	Global Positioning System
  - HDD/SSD Hard Drive - Solid State Drive
  -   TPM    Trusted Platform Module



---?image=/assets/images/slides/Slide23.JPG
@title[Where is UEFI firmware?]
<p align="right"><span class="gold" ><b>Where is UEFI firmware?</b></span></p>

Note:

- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 12  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 12 of PPT

- SOFTWARE STACK
- Specific examples




---?image=/assets/images/slides/Slide25.JPG
@title[In-the-wild Firmware Attacks]
<br>
<p align="left"><span class="gold" ><b>In-the-wild <br>Firmware Attacks</b></span></p>
<div class="left1">
<ul>
  <li><span style="font-size:0.8em" >Legacy Bootkits ( <a href="http://cdn5.esetstatic.com/eset/US/resources/docs/white-papers/white-papers-when-im-x64-bootkit-threat-evolution-2011.pdf">TDL4</a> , <a href="http://www.welivesecurity.com/wp-content/uploads/2013/04/gapz-bootkit-whitepaper.pdf">Gapz</a>. . .)</span>  </li>
  <li><span style="font-size:0.8em" ><a href="http://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/">Mebromi BIOS rootkit</a></span>  </li>
  <li><span style="font-size:0.8em" ><a href="https://www.virusbulletin.com/uploads/pdf/conference_slides/2010/OMurchu-VB2010.pdf">Stuxnet</a></span>  </li>
  <li><span style="font-size:0.8em" ><a href="https://securelist.com/files/2015/02/Equation_group_questions_and_answers.pdf">EQUATION Group </a>HDD firmware malware </span>  </li>
  <li><span style="font-size:0.8em" ><a href="http://www.intelsecurity.com/advanced-threat-research/content/data/HT-UEFI-rootkit.html">Hacking Team [ UEFI rootkit]</a></span>  </li>
  <li><span style="font-size:0.8em" ><a href="https://blog.malwarebytes.org/threat-analysis/2016/04/petya-ransomware/">Petya</a>MBR Ransomware</span>  </li>
  <li><span style="font-size:0.8em" >Legitimate BIOS “backdoors”: SuperFish, Computrace</span>  </li>
</ul>
</div>
<div class="right1">
<span style="font-size:01.0em" ><font color="cyan">&nbsp;</font></span>
</div>


Note:
- http://d2mlnkprj9wd81.cloudfront.net/sites/default/files/images/resource-centre/IFAW%20Wild%20Tiger.jpg
- http://www.ifaw.org/international/our-work/cats-and-dogs/creative-commons 
- Legacy:
	- TDL4 - trojan and bootkit created to steal data by intercepting a system's network traffic and searching for: banking usernames and passwords, credit card data, PayPal information, social security numbers, and other sensitive user data.[1] Following a series of customer complaints, Microsoft determined that Alureon caused a wave of BSoDs on some 32-bit Microsoft Windows systems. The update, MS10-015,[2] triggered these crashes by breaking assumptions made by the malware author(s).[

- TDL-4 is sometimes used synonymously with Alureon and is also the name of the rootkit that runs the botnet.

- Gapz_ For those who are curious why this threat is named Win32/Gapz here is the answer: the tag ‘GAPZ’ is used throughout all the binaries and shellcode for allocating memory. 
- Mebromi: 2011
- The infection starts with a small encrypted dropper that contains five crypted resource files: hook.rom, flash.dll, cbrom.exe, my.sys, bios.sys. The goal of these files will be presented later in this analysis.

- Stuxnet: 2010 Stuxnet is Targeted Targeting a Specific type of PLC Searches for a Specific Configuration - Stuxnet’s version intercepts
- reads and writes to the PLC

- EQUATION Group: 2001: 
- The Equation group is a highly sophisticated threat actor that has been engaged in multiple CNE (computer network exploitation) operations dating back to 2001, and perhaps as early as 1996. The Equation group uses multiple malware platforms, some of which surpass the well-known “Regin” threat in complexity and sophistication. The Equation group is probably one of the most sophisticated cyber attack groups in the world; and they are the most advanced threat actor we have seen. 

- Equation group because of their love for encryption algorithms and obfuscation strategies and the sophisticated methods used throughout their operations. 

- HackingTeam's UEFI Rootkit Details: Intel's Advanced Threat Research team (ATR) is the presence of what appears to be a UEFI-based persistent infection mechanism. ATR has been researching vulnerabilities related to system firmware and working with a community of firmware developers and platform manufacturers to mitigate these threats

- Petya MBR Ransomware- 2016 -  Petya’s ransom note states that it encrypts the full disk, but this is not true. Instead, it encrypts the master file table (MFT) so that the file system is not readable.

- SuperFish is a piece of software that is Pre-installed on some Lenovo computers. This software can break the HTTPS encryption used when the web browser on your computer communicates with websites that use the HTTPS protocol to protect sensitive information.Dec 1, 2015

- Computrace is software built into program laptops that were purchased as part of MCLA's Laptop Initiative. In the event your laptop is stolen, the Computrace software tracks the stolen computer and provides local police with the information they need to get it back.

 


---?image=/assets/images/slides/Slide27.JPG
@title[Why Attack Firmware?]
<p align="center"><span class="gold" ><b>Why Attack Firmware?</b></span></p>

Note:
- Brick 
- source: http://www.clipartpanda.com/clipart_images/brick-by-brick-clipart-1-71284827

- Firmware Attack Methods
- Categorize the different methods
- Why We are HERE!!!

- There are examples in the real world about attacks in each of these categories 




---?image=/assets/images/slides/Slide29.JPG
@title[Extreme Persistence]
### <p align="right"><span class="gold" ><b>Extreme Persistence</b></span></p>

Note:

- http://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&ved=0ahUKEwjg-8-9tY7TAhVSx2MKHZN2CpgQjRwIBw&url=http%3A%2F%2Fwww.elainebaileyinternational.com%2Fwordpress%2Fcategory%2Faccountability%2F&bvm=bv.151426398,d.cGc&psig=AFQjCNGTmCTOJCSqC446pVthXLAKMrSKoA&ust=1491519553033668



- User mode backdoor
- Kernel mode backdoor

- BIOS Level Back Door

- Takes control before any other software
- Stealth behavior
- Generally forgotten by almost all Antiviruses
- OS Independent (Runs outside the OS context)

### on the slide
- System firmware rootkit (in SMM or BIOS/UEFI)
- Replaces OS boot loader every boot

- Which patches OS kernel
- Firmware rootkit is protected by the hardware write protections
- Only way to fully remove the infection is to physically re-flash the flash “ROM” chip




---?image=/assets/images/slides/Slide31.JPG
@title[Stealth]
<br>
#### <p align="left"><span class="gold" ><b>Stealth</b></span></p>

Note:
#### Is Security Software real protection?

- Stealth CC
- https://farm1.staticflickr.com/8/7227778_c10e26cb79_o_d.jpg

-Security software usually doesn’t monitor ALL firmware on the platform
-How can software reliably tell infected from good firmware (FALSE - POSITIVE)
-Devices use obscure hardware interfaces to their firmware
-Which tool do we use to find BIOS/UEFI infection? And rootkit in firmware of SSD, NIC, EC, BMC, modem, USB thumb-drive, battery gauge, charger?




---?image=/assets/images/slides/Slide33.JPG
<!-- .slide: data-transition="none" -->
@title[Bypass Software Security – Full Disk ]
<p align="right"><span class="gold" ><b>Bypass Software Security – Full Disk</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="font-size:0.5em" ><a href="https://cansecwest.com/slides/2013/Evil%20Maid%20Just%20Got%20Angrier.pdf">Source</a>: Evil Maid Just Got Angrier: Why Full-Disk Encryption with TPM is not Secure on Many Systems</span>

Note:
- Security features like Full-Disk Encryption solutions rely on protections of the underlying firmware and hardware. Often system firmware (BIOS) doesn't use or incorrectly configures protections offered by hardware. 

- The PDF Link  demonstrates that software Full-Disk Encryption solutions are still subject to Evil Maid attacks when firmware fails to correctly utilize hardware protections, even when they rely on Trusted Platform Module to protect contents on the system drive from attacks that tamper with system firmware.



#### The PROBLEM
- Startup UEFI BIOS firmware at reset vector is inherently trusted
- To initiate chain of measurements or signature verification
- But it's firmware and can be updated

- If subverted or interrupted , all measurements in the chain can be forged - allowing firmware modifications to go undetected



#### Solution:
-  Just let BitLocker rely on all platform manufacturers to protect the UEFI
- BIOS from programmable SPI writes by malware,   and allow only signed UEFI BIOS updates, 



- protect authorized update software, 
- update the boot block (SEC/PEI code) securely, 
- correctly program and protect SPI Flash descriptor, 
- lock the SPI controller conguration, 
- AND NO BUGS ....

- Evil Maid 
- Attack Outline Against Encrypted OS Drive

1. While the owner is not watching and system is shut down.. 
2. adversary plugs in and boots into a USB thumb drive
3. which auto launches exploit directly modifying UEFI BIOS in unprotected SPI Flash
4. Gets out until owner notices someone is messing with the system 
5. Upon next boot, patched UEFI BIOS sends expected ’good’






+++?image=/assets/images/slides/Slide34.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Bypass Software Security – Full Disk 02 ]
<p align="right"><span class="gold" ><b>Bypass Software Security – Full Disk</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p align="right"><span style="font-size:0.5em" ><a href="https://cansecwest.com/slides/2013/Evil%20Maid%20Just%20Got%20Angrier.pdf">Source</a>: Evil Maid Just Got Angrier: Why Full-Disk Encryption with TPM is not Secure on Many Systems</span></p>

Note:
- Security features like Full-Disk Encryption solutions rely on protections of the underlying firmware and hardware. Often system firmware (BIOS) doesn't use or incorrectly configures protections offered by hardware. 

- The PDF Link  demonstrates that software Full-Disk Encryption solutions are still subject to Evil Maid attacks when firmware fails to correctly utilize hardware protections, even when they rely on Trusted Platform Module to protect contents on the system drive from attacks that tamper with system firmware.



#### The PROBLEM
- Startup UEFI BIOS firmware at reset vector is inherently trusted
- To initiate chain of measurements or signature verification
- But it's firmware and can be updated

- If subverted or interrupted , all measurements in the chain can be forged - allowing firmware modifications to go undetected



#### Solution:
-  Just let BitLocker rely on all platform manufacturers to protect the UEFI
- BIOS from programmable SPI writes by malware,   and allow only signed UEFI BIOS updates, 



- protect authorized update software, 
- update the boot block (SEC/PEI code) securely, 
- correctly program and protect SPI Flash descriptor, 
- lock the SPI controller conguration, 
- AND NO BUGS ....

- Evil Maid 
- Attack Outline Against Encrypted OS Drive

1. While the owner is not watching and system is shut down.. 
2. adversary plugs in and boots into a USB thumb drive
3. which auto launches exploit directly modifying UEFI BIOS in unprotected SPI Flash
4. Gets out until owner notices someone is messing with the system 
5. Upon next boot, patched UEFI BIOS sends expected ’good’






---?image=/assets/images/slides/Slide36.JPG
@title[Bypass Software Security – UEFI Secure Boot ]
<p align="right"><span class="gold" ><b>Bypass Software Security – UEFI Secure Boot</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p align="right"><span style="font-size:0.5em" ><a href="https://media.blackhat.com/us-13/us-13-Bulygin-A-Tale-of-One-Software-Bypass-of-Windows-8-Secure-Boot-Slides.pdf">Source</a>: A Tale of One Software Bypass of Windows Secure Boot</span></p>

Note:

- The UEFI specification defines secure booting of the operating system, helping protect against bootkits and other boot time attacks. However, robust implementation of Secure Boot in the system firmware is not always trivial and mistakes in the implementation can undermine protections offered by Secure Boot. 

- In Windows systems  UEFI Secure Boot is an important step towards securing platforms from malware compromising boot sequence before the OS. However, there are certain mistakes platform vendors sometimes make which can completely undermine protections offered by Secure Boot. 

- The linked PDF will demonstrate an example of full software bypass of Windows 8 Secure Boot due to such mistakes on some of the latest platforms and explain how those mistakes can be avoided

- So UEFI firmware updates are signed but firmware is directly writeable in SPI flash? So is NVRAM with EFI variables. Hmm… What could go wrong? 
- Hint: Malware could patch DXE Image Verification driver in ROM or it could change persistent Secure Boot keys/configuration in NVRAM 

- Malware could patch the NvRam Variable “SecureBoot”

- Source: A Tale of One Software Bypass of Windows Secure Boot : https://media.blackhat.com/us-13/us-13-Bulygin-A-Tale-of-One-Software-Bypass-of-Windows-8-Secure-Boot-Slides.pdf 




---?image=/assets/images/slides/Slide38.JPG
@title[Bypass Software Security – Virtual Machine Manager ]
<p align="right"><span class="gold" ><b>Bypass Software Security <br>– Virtual Machine Manager</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:40%" align="right"><span style="font-size:0.5em" ><a href="http://www.intelsecurity.com/advanced-threat-research/content/AttackingHypervisorsViaFirmware_bhusa15_dc23.pdf">Source</a>: Attacking Hypervisors via Firmware and Hardware</span></p>

Note:

- http://www.intelsecurity.com/advanced-threat-research/content/AttackingHypervisorsViaFirmware_bhusa15_dc23.pdf

- VMM Isolation there is an assumed protection

- The PDF Link is a  research presentation that builds on a study  of hypervisor implementations as well as vulnerabilities in system firmware. 
- If the hypervisor does not fully isolate the system firmware from attacks within a guest VM, security issues in the underlying system may be exposed. 

- This research presented multiple real-world bypasses of hypervisor security using already-known firmware vulnerabilities that happened to be exposed.

- Software Isolation 
- CPU / SoC: traps to hypervisor (VM Exits), MSR & I/O permissions bitmaps, rings (PV)… 
- Memory / MMIO: hardware page tables (e.g. EPT, NPT), software shadow page tables 

- Devices Isolation 
- CPU / SoC: interrupt remapping 
- Memory / MMIO: IOMMU, No-DMA ranges 


- Protecting Memory with HW Assisted Paging 

#### VMM “forensics” 
- With the help of a rootkit in firmware any VM guest can extract all information about hypervisor and other VMs … and just from memory 
  - VMCS structures, MSR and I/O bitmaps for each VM guest 
  - EPT for each VM guest 
  - Regular page tables for hypervisor and each VM guest 
  - IOMMU pages tables for each IOMMU device 
  - Full hypervisor memory map, VM exit handler… 
  - Real hardware configuration (registers for real PCIe devices, MMIO contents…) 


- Did you know that VMMs emulate virtual devices of other VMMs? 

- Exploiting firmware SMI handler to attack VMM 

- Attacking VMM by proxying through SMI handler 

####  flashed rootkited
- We flashed rootkited part of firmware image from within a root partition to install the rootkit 
- The system doesn’t properly protect firmware in SPI flash memory so we could bypass write-protection 
- Finally more systems protect firmware on the flash memory 
  - common.bios_wp - CHIPSEC module to test write-protection 
- Malware can exploit vulnerabilities in firmware to install a rootkit on such systems 

#### Sometimes attacker doesn’t need a vulnerability in firmware…
- When VMM grants VM direct access to firmware or hardware interfaces 
- VM exploit doesn’t always need to exploit firmware first through these interfaces 
- It may use firmware or hardware as a confused deputy and attack VMM through some function on behalf of firmware



---?image=/assets/images/slides/Slide40.JPG
@title[Unfettered Access to Hardware - DRAM ]
<p align="right"><span class="gold" ><b>Unfettered Access to Hardware - DRAM</b></span></p>
<p style="line-height:50%" align="right"><span style="font-size:0.5em" ><a href="http://www.syssec-project.eu/media/page-media/23/syssec2011-s1.4-sang.pdf">Source</a> :I/O Attacks in <br>Intel-PC Architecture ...</span></p>


Note:

#### Direct Memory Access  DMA mechanism

- A DMA attack is a type of side channel attack in computer security, in which an attacker can penetrate a computer or other device, by exploiting the presence of high-speed expansion ports that permit direct memory access ("DMA").
 
- DMA is included in a number of connections, because it lets a connected device (such as a camcorder, network card, storage device or other useful accessory or internal PC card) transfer data between itself and the computer at the maximum speed possible, by using direct hardware access to read or write directly to main memory without any operating system supervision or interaction. 

- The legitimate uses of such devices have led to wide adoption of DMA accessories and connections, but an attacker can equally use the same facility to create an accessory that will connect using the same port, and can then potentially gain direct access to part or all of the physical memory address space of the computer, bypassing all OS security mechanisms and any lock screen, to read all that the computer is doing, steal data or cryptographic keys, install or run spyware and other exploits, or modify the system to allow backdoors or other malware.



- What does Direct Memory Access mechanism stand for ?
- I/O mechanism that enables an I/O controller
- to perform directly a data transfer to/from the main memory without OS
- to offload the CPU of these transfers
- relies on a dedicated DMA engine

- Examples of I/O controllers using DMA:
network controllers (WiFi, Ethernet, . . . )
  - ! e.g., to transfer network frames into/from the main memory disk controllers
  - ! e.g., to transfer files into/from the main memory
- graphic controllers
  - ! e.g., to transfer textures, buffer objects from the main memory 5/

- DMA attacks aiming at the main memory:
  - attack (confidentiality & integrity) on software components
  - modifications made in the main memory can be detected

- Examples: [Dornseif 04, Becher 05, Carrier 04, Nick L. Petroni 04,
- Maynor 05, Boileau 06, Duflot 07, Duflot 10, Aumaitre 09, Piegdon 07


#### Mitigations
-Physical security – 
-Secure boot
-IOMMU – I/O Memory Management Unit – Intel® VT-d can use them to block I/O transactions that have not been allowed. However,    IOMMUs mostly are used instead to give guest virtual machines passthrough access to host hardware.
- OS selectively locking out devices
- Never allow sensitive data to be stored in Memory unencrypted


- Source: I/O Attacks in Intel-PC Architecture and Countermeasures by F. Lone Sang et al
- http://www.syssec-project.eu/media/page-media/23/syssec2011-s1.4-sang.pdf





---?image=/assets/images/slides/Slide42.JPG
@title[Unfettered Access to Hardware - DRAM ]
<p align="right"><span class="gold" ><b>Unfettered Access to Hardware - DRAM</b></span></p>
<p style="line-height:50%" align="right"><span style="font-size:0.5em" ><a href="http://www.syssec-project.eu/media/page-media/23/syssec2011-s1.4-sang.pdf">Source</a> :I/O Attacks in <br>Intel-PC Architecture ...</span></p>



Note:

- Source: I/O Attacks in Intel-PC Architecture and Countermeasures by F. Lone Sang et al
- http://www.syssec-project.eu/media/page-media/23/syssec2011-s1.4-sang.pdf


####  Direct Memory Access  DMA mechanism

- A DMA attack is a type of side channel attack in computer security, in which an attacker can penetrate a computer or other device, by exploiting the presence of high-speed expansion ports that permit direct memory access ("DMA").

- DMA attacks aiming at I/O controllers’ internal memory:
  - exploit I/O controllers’ ressources (memory, features, . . . )
  - no modifications in the main memory, hard to detect
    - Examples: [Dornseif 04, Triulzi 08, Triulzi 10, Lone Sang 11a]

#### Mitigations
-Physical security – 
-Secure boot
-IOMMU – I/O Memory Management Unit – Intel® VT-d can use them to block I/O transactions that have not been allowed. However,    IOMMUs mostly are used instead to give guest virtual machines passthrough access to host hardware.
- OS selectively locking out devices
- Never allow sensitive data to be stored in Memory unencrypted



---?image=/assets/images/slides/Slide44.JPG
@title[Unfettered Access to Hardware – HDD/SSD ]
<br>
<p align="right"><span class="gold" ><b>Unfettered Access to Hardware – HDD/SSD</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:50%" align="right"><span style="font-size:0.5em" ><a href="http://www.pcworld.com/article/2884952/equation-cyberspies-use-unrivaled-nsastyle-techniques-to-hit-iran-russia.html">Source</a> : PC World – Destroying your hard drive is the only<br> way to stop this super advanced malware</span></p>

Note:

- A cyberespionage group with a toolset similar to ones used by U.S. intelligence agencies has infiltrated key institutions in countries including Iran and Russia, utilizing a startlingly advanced form of malware that is impossible to remove once it's infected your PC

- From PC WORLD

- Kaspersky Lab released a report in Feb 2015,  that said the tools were created by the “Equation” group, which it stopped short of linking to the U.S. National Security Agency. 

- Infirm firmware
- Kaspersky’s most striking finding is Equation’s ability to infect the firmware of a hard drive, or the low-level code that acts as an interface between hardware and software. 

- The malware reprograms the hard drive’s firmware, creating hidden sectors on the drive that can only be accessed through a secret API (application programming interface). Once installed, the malware is impossible to remove: disk formatting and reinstalling the OS doesn’t affect it, and the hidden storage sector remains. 
- “Theoretically, we were aware of this possibility, but as far as I know this is the only case ever that we have seen of an attacker having such an incredibly advanced capability,” said Costin Raiu, director of Kaspersky Lab’s global research and analysis team, in a phone interview Monday. 

- Report link: http://25zbkz3k00wn2tp5092n6di7b5k.wpengine.netdna-cdn.com/files/2015/02/Equation_group_questions_and_answers.pdf 

- Source: PC World – Destroying your hard drive is the only way to stop this super advanced malware : http://www.pcworld.com/article/2884952/equation-cyberspies-use-unrivaled-nsastyle-techniques-to-hit-iran-russia.html 



---?image=/assets/images/slides/Slide46.JPG
@title[Unfettered Access to Hardware – Etc. ]
<p align="right"><span class="gold" ><b>Unfettered Access to Hardware – Etc.</b></span></p>
<br>

Note:

- Wifi image source:  https://commons.wikimedia.org/wiki/File%3AWIFI_icon.svg - By Canopus49 (Own work) [CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons

- NIC – Network interface controller

- EC –    embedded controllers 
- BMC – Baseboard Management Component



---?image=/assets/images/slides/Slide48_1.JPG
@title[Making System Unbootable (Bricking) ]
<p align="right"><span class="gold" ><b>Making System Unbootable (Bricking)</b></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p align="right"><span style="font-size:0.5em" ><a href="http://www.sophos.com/en-us/press-office/press-releases/1998/06/pr_uk_19980630cih.aspx">Source</a> : CIH virus, was first discovered in 1998</span></p>

Note:

- Source http://www.sophos.com/en-us/press-office/press-releases/1998/06/pr_uk_19980630cih.aspx
- The CIH virus, also known as Chernobyl, was first discovered in 1998, and quickly became one of the most commonly encountered viruses in the wild.

- CIH virus has the capacity to overwrite system start-up routines, as well as wiping data on hard disks. The virus attacks the BIOS, needed to boot up the computer, something which no previous virus has managed to do.


- The Real Chernobyl Nuclear melt down
- Before April 26th 1986, Chernobyl was a word hardly anybody ever heard. But within days it became the only word on peoples minds. In what was first passed off as "nothing" quickly escalated as reports from outside the Soviet Union filtered in what was to become the worst Nuclear Power Plant disaster in history.

- Chernobyl image sign source: https://farm6.staticflickr.com/5186/5661310269_0e42fa50ea_o_d.jpg
- Chernobyl areal view: http://crooksandliars.com/gordonskene/other-plans-gone-wrong-chernobyl-april


---?image=/assets/images/slides/Slide50.JPG
@title[Pre-Boot Threats ]
<br>
<br>
<p align="left"><span class="gold" ><b>Pre-Boot<br>Threats </b></span></p>

Note:


---?image=/assets/images/slides/Slide52.JPG
@title[Summary - Platform Firmware Security – Why is it important? ]
<p align="right"><span class="gold" ><b>Summary <br>Platform Firmware Security – Why is it important?</b></span></p>
<br>
<br>
<br>
<br>

Note:
There are several Firmware attack methods – and cyber hackers will be continually finding more. We need to be able to recognize where Firmware is vulnerable to help prevent attacks on firmware.<br>In Summary: This section is the “WHY WE ARE HERE”




