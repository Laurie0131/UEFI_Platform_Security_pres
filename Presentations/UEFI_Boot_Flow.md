
@title[UEFI boot flow with the TM Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI boot flow</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI boot flow with the threat model</span>

Note:
  UEFI_boot_flow.md for UEFI / EDK II Training  UEFI boot flow with the TM

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



---?image=/assets/images/slides/Slide28_1.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Execution Flow]
<p align="right"><span class="gold" >@size[1.1em](<b>UEFI Boot Execution Flow</b>)</span></p>


@snap[south span-80 fragment]
@box[bg-red-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:01.1em; font-weight: bold;" >What Could Possibly Go Wrong???<br>&nbsp;</span></p>)
@snapend 


@snap[north-west span-100 fragment]
<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[bomb fa-2x gp-bullet-red2]<br>
@fa[bomb fa-2x gp-bullet-red2]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[bomb fa-2x gp-bullet-red2]<br>
<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[bomb fa-2x gp-bullet-red2]<br>

@snapend 

Note:
#### List of potential areas to attack:
- BootGuard (SPI and Memory attack?)
- Capsule update
- S3 Resume
- SMM
- Secure variables
- Boot APIs & Runtime APIs
- SPI attack with BIOSGuard disabled?
- ACPI?
- SMM COM buffer
- OS Boot loader 

- Confirm that any calls to unsafe string functions are replaced by safe string functions.

- Hardware boot sequence before the reset vector
- External power supplied (e.g. 12V) to the system and settles 
- Power is driven in a sequence to multiple processor and chipset voltage rails
- Platform clocks are derived from external clock and oscillators
- Processor reset signal is de-asserted
- Power management logic in the CPU executes reset sequence (samples fuses, handshake with the PCH, reads Power-On configuration etc.)
- Power management logic brings cores out of reset
- Processor cores execute reset microcode (initializes x86 state, parses FW interface table, etc.)
- RESET VECTOR - Finally, reset microcode fetches the first instruction at physical address FFFFFFF0h known as reset vector





---?image=/assets/images/slides/Slide31_1.JPG
@title[UEFI & Platform Initialization Task Flow]
<p align="right"><span class="gold" >@size[1.1em](<b>UEFI & Platform Initialization Task Flow</b>)</span></p>

@snap[south-west span-55]
<p style="line-height:50%" align="left"><span style="font-size:0.3em" >
<sup>1</sup>S-CRTM - static core root of trust for measurement
</span></p>
@snapend

@snap[north-east span-75 fragment]
<br>
<br>
<br>
<p style="line-height:40%"  align="left"><span style="font-size:0.5em" >
S-CRTM<sup> 1</sup>; Init caches/MTRRs; Cache-as-RAM (NEM); Recovery; TPM Init
</span></p>
@snapend

@snap[north-east span-60 fragment]
<br>
<br>
<br>
<br>
<br>
<p style="line-height:40%" align="left"><span style="font-size:0.5em" >
S-CRTM: Measure DXE/BDS<br>
Early CPU/PCH Init<br>
Memory (DIMMs, DRAM) Init<br>
Boot Mode (normal, S3, Recovery, Capsule update)
</span></p>
@snapend



@snap[north-east span-50  fragment]
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:40%" align="left"><span style="font-size:0.5em" ><br><br>
UEFI “Core” functionality, Continue initialization of platform & devices Enum FV, dispatch drivers (network, I/O, service..), Produce Boot and Runtime Services, SMM Initialization
</span></p>
@snapend


@snap[north-east span-30 fragment]
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:30%" align="left"><span style="font-size:0.4em" ><br>
Boot Manager (Select Boot Device)<br>
EFI Shell/Apps; OS Boot Loader(s); Option ROM
</span></p>
@snapend

@snap[north-west span-45 fragment]
<br>
<br>
<br>

<br>
<br>
<br>

<br>
<br>
<br>

<br>
<br>
<br>
<p style="line-height:30%" align="right"><span style="font-size:0.4em" >
ACPI, UEFI SystemTable, SMBIOS table,<br>
Lock resources 
</span></p>
@snapend

@snap[north-west span-60 fragment]
<br>
<br>
<br>

<br>
<br>
<br>

<br>
<br>
<br>

<br>
<br>
<br>
<br>
<br>
<p style="line-height:30%" align="right"><span style="font-size:0.4em" >
ExitBootServices. Minimal <br>UEFI services(Variable, Capsule)
</span></p>
@snapend


Note:

- S-CRTM is a ”static core root of trust for measurement.” The S-CRTM is the portion of the platform firmware that must be „implicitly trusted.‟ The S-CRTM makes the first measurements, starts TPM, and detects physical presence per the TCG privacy model.
ExitBootServices. Minimal UEFI services (Variable, Capsule



---?image=/assets/images/slides/Slide32_1.JPG
@title[Firmware Attack Surfaces]
<p align="right"><span class="gold" ><b>Firmware Attack Surfaces</b></span></p>

@snap[south-east span-35 fragment]
![Yellow-arrow](/assets/images/LftYellowArrow.png)
@snapend 

Note:


#### What could go wrong !!

- Unsafe Coding Practices - Confirm that any calls to unsafe string functions are replaced by safe string functions.

- Option ROMs – 
- Shell – Apps
- APIs  - Standard APIs get attacked
- SMM – A common one 
- Firmware Update interfaces
- Firmware Vendor Hooks
- Server Management Interfaces  (RAS???)

##### PIT FALLS

- Field Updatable
- BIOS, like other firmware, often needs to be updated in the field post-deployment.

- Standard APIs
- BIOS unlike many other custom firmware implementations is more and more being developed using standard UEFI interfaces.
- These are published (hint, hint)

- Intimate Platform control Points
- Subverting BIOS opens up direct and deep handles on a platform which can be exploited without knowledge of higher-level software (SMM).

- Option ROMs
- Plug in that PCIe card and invite its Option ROM to the party.
- OROM code pulled in by BIOS at boot time

---
@title[Goals of security architecture and assets that are protected ]
<p align="right"><span class="gold" >@size[1.1em](<b>Goals of security architecture and assets<br>that are protected </b>)</span></p>
@snap[north-east span-50 ]
<br>
<br>
<p style="line-height:35%" align="right"><span style="font-size:0.4em" ><a href="http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf">NIST SP 800-33</a> – IT Security Objectives <br>
Availability, Integrity, Confidentiality,  Accountability, Assurance  
</span></p>
@snapend

@snap[north span-80 ]
<br>
<br>
<br>
<p style="line-height:50%" >&nbsp;</p>
@box[bg-grey-25  text-white rounded](<p style="line-height:70%" ><span style="font-size:0.9em; font-weight: bold;" ><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
<br>
@snapend

@snap[north span-65 ]
<br>
<br>
<br>
<p style="line-height:50%" ><br><br>&nbsp;</p>
<p style="line-height:70%" align="left"><span style="font-size:0.9em" >
<b>The goal of information technology security: </b>
</span></p>
<p style="line-height:70%" align="left"><span style="font-size:0.7em" >
Enable an organization to meet all of its mission/business objectives by implementing systems with due care consideration of IT-related risks to the organization, its partners and customers. 
</span></p>
@snapend



Note:

- source : https://firmware.intel.com/sites/default/files/uefi-pi-tcg-firmware-white-paper%5B1%5D.pdf fig 3   assurance - NON – Ra PU DEE A Tion

- How do does industry help us solve the problem.
 - Set GOALs  and OBJECTIVES

- NIST - National Institute of Standards and Technology 


- Key Concept Security Goal- The goal of information technology security is to: Enable an organization to meet all of its mission/business objectives by implementing systems with due care consideration of IT-related risks to the organization, its partners and customers. 

- The security goal can be met through the following security objectives:
- s started with: 
- The CIA triad of Confidentiality, Integrity, and Availability is at the heart of information security 
- NOT Central Intelligent Agency

- Then NIST SP 800-33 further defined these 5.
- See also : CIAAN https://securopia.wordpress.com/2011/08/25/security-models-cia-and-ciaan/

- Underlying Technical Models for Information Technology Security NIST SP 800-33

- National Institute of Standards and Technology NIST 800 33 pdf  sec 2.0 Security Goal and Objectives http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf

- Security Goal The goal of information technology security is to: Enable an organization to meet all of its mission/business objectives by implementing systems with due care consideration of IT-related risks to the organization, its partners and customers. 

- The security goal can be met through the following security objectives:

#### CIA
1. Availability (of systems and data for intended use only) Availability is a requirement intended to assure that systems work promptly and service is not denied to authorized users. This objective protects against: • Intentional or accidental attempts to either: − perform unauthorized deletion of data or − otherwise cause a denial of service or data. • Attempts to use system or data for unauthorized purposes Availability is frequently an organization’s foremost security objective. 
2. Integrity (of system and data) Integrity has two facets: • Data integrity (the property that data has not been altered in an unauthorized manner while in storage, during processing, or while in transit) or • System integrity (the quality that a system has when performing the intended function in an unimpaired manner, free from unauthorized manipulation). Integrity is commonly an organization’s most important security objective after availability. 
3. Confidentiality (of data and system information) Confidentiality is the requirement that private or confidential information not be disclosed to unauthorized individuals. Confidentiality protection applies to data in storage, during processing, and while in transit. For many organizations, confidentiality is frequently behind availability and integrity in terms of importance. Yet for some systems and for specific types of data in most systems (e.g., authenticators), confidentiality is extremely important. 
4. Accountability (to the individual level) Accountability is the requirement that actions of an entity may be traced uniquely to that entity. Accountability is often an organizational policy requirement and directly supports nonrepudiation, deterrence, fault isolation, intrusion detection and prevention, and after-action recovery and legal action. 
5. Assurance (that the other four objectives have been adequately met) Assurance is the basis for confidence that the security measures, both technical and operational, work as intended to protect the system and the information it processes. The other four security objectives (integrity, availability, confidentiality, and accountability) have been adequately met by a specific implementation when: • required functionality is present and correctly implemented, • there is sufficient protection against unintentional errors (by users or software), and • there is sufficient resistance to intentional penetration or by-pass. Assurance is essential; without it the other objectives are not met. However, assurance is a continuum; the amount of assurance needed varies between systems.

+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Goals of security architecture and assets that are protected  02]
<p align="right"><span class="gold" >@size[1.1em](<b>Goals of security architecture and assets<br>that are protected </b>)</span></p>
@snap[north-east span-50 ]
<br>
<br>
<p style="line-height:35%" align="right"><span style="font-size:0.4em" ><a href="http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf">NIST SP 800-33</a> – IT Security Objectives <br>
Availability, Integrity, Confidentiality,  Accountability, Assurance  
</span></p>
@snapend

@snap[north span-80 ]
<br>
<br>
<br>
<p style="line-height:50%" >&nbsp;</p>
@box[bg-grey-25  text-white rounded](<p style="line-height:70%" ><span style="font-size:0.9em; font-weight: bold;" ><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
<br>
@snapend

@snap[north span-75 ]
<br>
<br>
<br>
<br>
<br>
<table id="recTable">
	<tr class="fragment">
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.8em" ><b><u>C</u>onfidentiality</b></span></p></td>
		<td align="left" bgcolor="#bfbfbf" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><font color="black">Protect against unauthorized access</font></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.8em" ><b><u>I</u>ntegrity</b></span></p></td>
		<td align="left" bgcolor="#bfbfbf" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><font color="black">Protection of Content & Quality</font></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.8em" ><b><u>A</u>vailability</b></span></p></td>
		<td align="left" bgcolor="#bfbfbf" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><font color="black">Ensure access</font></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.8em" ><b>Accountability</b></span></p></td>
		<td align="left" bgcolor="#bfbfbf" height=".0025"><p style="line-height:040%"><span style="font-size:0.6em" ><font color="black">Also Authenticity -  traced uniquely to the source entity</font></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.8em" ><b>Assurance</b></span></p></td>
		<td align="left" bgcolor="#bfbfbf" height=".0025"><p style="line-height:040%"><span style="font-size:0.6em" ><font color="black">Guarantee on the correctness, Non-repudiation</font></span></p></td>
	</tr>
</table>
@snapend

@snap[south span-85 fragment]
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em">All of these objectives are interdependent with Assurance<br>&nbsp;</span></p>)
@snapend

Note:

- source : https://firmware.intel.com/sites/default/files/uefi-pi-tcg-firmware-white-paper%5B1%5D.pdf fig 3   assurance - NON – Ra PU DEE A Tion

- How do does industry help us solve the problem.
 - Set GOALs  and OBJECTIVES

- NIST - National Institute of Standards and Technology 


- Key Concept Security Goal- The goal of information technology security is to: Enable an organization to meet all of its mission/business objectives by implementing systems with due care consideration of IT-related risks to the organization, its partners and customers. 

- The security goal can be met through the following security objectives:
- s started with: 
- The CIA triad of Confidentiality, Integrity, and Availability is at the heart of information security 
- NOT Central Intelligent Agency

- Then NIST SP 800-33 further defined these 5.
- See also : CIAAN https://securopia.wordpress.com/2011/08/25/security-models-cia-and-ciaan/

- Underlying Technical Models for Information Technology Security NIST SP 800-33

- National Institute of Standards and Technology NIST 800 33 pdf  sec 2.0 Security Goal and Objectives http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf

- Security Goal The goal of information technology security is to: Enable an organization to meet all of its mission/business objectives by implementing systems with due care consideration of IT-related risks to the organization, its partners and customers. 

- The security goal can be met through the following security objectives:

#### CIA
1. Availability (of systems and data for intended use only) Availability is a requirement intended to assure that systems work promptly and service is not denied to authorized users. This objective protects against: • Intentional or accidental attempts to either: − perform unauthorized deletion of data or − otherwise cause a denial of service or data. • Attempts to use system or data for unauthorized purposes Availability is frequently an organization’s foremost security objective. 
2. Integrity (of system and data) Integrity has two facets: • Data integrity (the property that data has not been altered in an unauthorized manner while in storage, during processing, or while in transit) or • System integrity (the quality that a system has when performing the intended function in an unimpaired manner, free from unauthorized manipulation). Integrity is commonly an organization’s most important security objective after availability. 
3. Confidentiality (of data and system information) Confidentiality is the requirement that private or confidential information not be disclosed to unauthorized individuals. Confidentiality protection applies to data in storage, during processing, and while in transit. For many organizations, confidentiality is frequently behind availability and integrity in terms of importance. Yet for some systems and for specific types of data in most systems (e.g., authenticators), confidentiality is extremely important. 
4. Accountability (to the individual level) Accountability is the requirement that actions of an entity may be traced uniquely to that entity. Accountability is often an organizational policy requirement and directly supports nonrepudiation, deterrence, fault isolation, intrusion detection and prevention, and after-action recovery and legal action. 
5. Assurance (that the other four objectives have been adequately met) Assurance is the basis for confidence that the security measures, both technical and operational, work as intended to protect the system and the information it processes. The other four security objectives (integrity, availability, confidentiality, and accountability) have been adequately met by a specific implementation when: • required functionality is present and correctly implemented, • there is sufficient protection against unintentional errors (by users or software), and • there is sufficient resistance to intentional penetration or by-pass. Assurance is essential; without it the other objectives are not met. However, assurance is a continuum; the amount of assurance needed varies between systems.


---
@title[What to build & defend – Rationale for a threat model]
<p align="right"><span class="gold" >@size[1.1em](<b>What to build & defend <br> – Rationale for a threat model</b>)</span></p>
@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:80%" align="left"><span style="font-size:0.9em" ><br>
"@color[yellow](My house is secure)"is almost meaningless<br>
@size[.7em](&bull;&nbsp;Against a burglar? Against a meteor strike? A thermonuclear device?)<br>
"@color[yellow](My system is secure)"is almost meaningless<br>
@size[.7em](&bull;&nbsp;Against what? To what extent?)<br>
</span></p>
@snapend

@snap[north-west span-100 fragment ]
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:70%" align="left"><span style="font-size:0.8em" ><br>
Threat modeling is a process to define the goals and constraints of a (software) security solution<br>
@size[.7em](&bull;&nbsp;Translate user requirements to security requirements )
</span></p>
@snapend

@snap[north-west span-100 fragment ]
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.8em" ><br>
We use threat modeling for our UEFI / PI codebase<br>
@size[.7em](&bull;&nbsp; We believe the process and findings are applicable to driver implementations as well as UEFI implementations in general)<br>
</span></p>
@snapend

@snap[south span-85 fragment]
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em">We Need to protect our Assets from Threats<br>&nbsp;</span></p>)
@snapend

Note:
- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 53  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 53 of PPT


- The KEY POINT is we need to protect our Assets from threats 



---?image=/assets/images/slides/Slide69.JPG
<!-- .slide: data-transition="none" -->
@title[We don’t always get to  choose our Assets]
<p align="right"><span class="gold" ><b>We don’t always get to  choose our Assets</b></span></p>

Note:
- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 55  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 54-55 of PPT




#### BIOS Flash
- NIST SP800-147 says
- Lock code flash except for update before Exit Mfg Auth
- Signed update (>= RSA2048, SHA256)
- High quality signing servers
- Without back doors (“non-bypassability”)
- Threats
- PDOS – Permanent Denial of Service
- System into inefficient room heater
- Elevation of privilege
- Owning the system at boot is an advantage to a virus
- Known attacks
- CIH / Chernobyl 1999-2000
- Mebroni 2010
- Mitigations include
- Reexamining flash protection methods – use the best even if its new
- Using advanced techniques to locate and remove (un)intentional backdoors

#### SMM is valuable because
- It’s invisible to Anti Virus, etc
- SMM sees all of system RAM
- Not too different from PCI adapter device firmware
- Threats
- Elevation
- View secrets or own the system by subverting RAM
- Known attacks
- See e.g Duflot, Legbacore
- Mitigations include
- Validate “external” / “untrusted” input
- Remove calls from inside SMM to outside SMM

#### BOOT FLOW
- Secure boot
- Authenticated variables
- Based on the fundamental Crypto being correct
- Correct location for config data
- Threats
- Run unauthorized op roms, boot loaders
- PDOS systems with bad config variables
- Known attacks
- Mitigations include
- Sanity check config vars before use, use defaults
- Reviews, fuzz checking, third party reviews, etc.

####RESUME From S3
- ACPI says that we return the system to the S5S0 configuration at S3S0
- Must protect the data structures we record the cold boot config in
- Threats
- Changing data structures could cause security settings to be incorrectly configured leaving S3
- Reopen the other assets’ mitigated threats 
- Known attacks
- Mitigations include
- Store data in SMM -or-
- Store hash of data structures and refuse to resume if the hashes don’t compare

#### BUILD TOOLS
- Tools create the resulting firmware
- Rely on third party tools and home grown tools
- Incorrect or attacked tools leave vulnerabilities
- Threats
- Disabled signing, for example
- Known attacks
- See e.g. Reflections on Trust, Ken Thompson**
- Mitigation
- Difficult: For most tools, provided as source code
- Review for correct implementation
- Use static, dynamic code analysis tools
- PyLint for Python, for example




+++?image=/assets/images/slides/Slide70.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[We don’t always get to  choose our Assets 02]
<p align="right"><span class="gold" ><b>We don’t always get to  choose our Assets</b></span></p>

Note:
- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 55  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 54-55 of PPT




#### BIOS Flash
- NIST SP800-147 says
- Lock code flash except for update before Exit Mfg Auth
- Signed update (>= RSA2048, SHA256)
- High quality signing servers
- Without back doors (“non-bypassability”)
- Threats
- PDOS – Permanent Denial of Service
- System into inefficient room heater
- Elevation of privilege
- Owning the system at boot is an advantage to a virus
- Known attacks
- CIH / Chernobyl 1999-2000
- Mebroni 2010
- Mitigations include
- Reexamining flash protection methods – use the best even if its new
- Using advanced techniques to locate and remove (un)intentional backdoors

#### SMM is valuable because
- It’s invisible to Anti Virus, etc
- SMM sees all of system RAM
- Not too different from PCI adapter device firmware
- Threats
- Elevation
- View secrets or own the system by subverting RAM
- Known attacks
- See e.g Duflot, Legbacore
- Mitigations include
- Validate “external” / “untrusted” input
- Remove calls from inside SMM to outside SMM

#### BOOT FLOW
- Secure boot
- Authenticated variables
- Based on the fundamental Crypto being correct
- Correct location for config data
- Threats
- Run unauthorized op roms, boot loaders
- PDOS systems with bad config variables
- Known attacks
- Mitigations include
- Sanity check config vars before use, use defaults
- Reviews, fuzz checking, third party reviews, etc.

####RESUME From S3
- ACPI says that we return the system to the S5S0 configuration at S3S0
- Must protect the data structures we record the cold boot config in
- Threats
- Changing data structures could cause security settings to be incorrectly configured leaving S3
- Reopen the other assets’ mitigated threats 
- Known attacks
- Mitigations include
- Store data in SMM -or-
- Store hash of data structures and refuse to resume if the hashes don’t compare

#### BUILD TOOLS
- Tools create the resulting firmware
- Rely on third party tools and home grown tools
- Incorrect or attacked tools leave vulnerabilities
- Threats
- Disabled signing, for example
- Known attacks
- See e.g. Reflections on Trust, Ken Thompson**
- Mitigation
- Difficult: For most tools, provided as source code
- Review for correct implementation
- Use static, dynamic code analysis tools
- PyLint for Python, for example




+++?image=/assets/images/slides/Slide71.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[We don’t always get to  choose our Assets 03]
<p align="right"><span class="gold" ><b>We don’t always get to  choose our Assets</b></span></p>

Note:
- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 55  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 54-55 of PPT




#### BIOS Flash
- NIST SP800-147 says
- Lock code flash except for update before Exit Mfg Auth
- Signed update (>= RSA2048, SHA256)
- High quality signing servers
- Without back doors (“non-bypassability”)
- Threats
- PDOS – Permanent Denial of Service
- System into inefficient room heater
- Elevation of privilege
- Owning the system at boot is an advantage to a virus
- Known attacks
- CIH / Chernobyl 1999-2000
- Mebroni 2010
- Mitigations include
- Reexamining flash protection methods – use the best even if its new
- Using advanced techniques to locate and remove (un)intentional backdoors

#### SMM is valuable because
- It’s invisible to Anti Virus, etc
- SMM sees all of system RAM
- Not too different from PCI adapter device firmware
- Threats
- Elevation
- View secrets or own the system by subverting RAM
- Known attacks
- See e.g Duflot, Legbacore
- Mitigations include
- Validate “external” / “untrusted” input
- Remove calls from inside SMM to outside SMM

#### BOOT FLOW
- Secure boot
- Authenticated variables
- Based on the fundamental Crypto being correct
- Correct location for config data
- Threats
- Run unauthorized op roms, boot loaders
- PDOS systems with bad config variables
- Known attacks
- Mitigations include
- Sanity check config vars before use, use defaults
- Reviews, fuzz checking, third party reviews, etc.

####RESUME From S3
- ACPI says that we return the system to the S5S0 configuration at S3S0
- Must protect the data structures we record the cold boot config in
- Threats
- Changing data structures could cause security settings to be incorrectly configured leaving S3
- Reopen the other assets’ mitigated threats 
- Known attacks
- Mitigations include
- Store data in SMM -or-
- Store hash of data structures and refuse to resume if the hashes don’t compare

#### BUILD TOOLS
- Tools create the resulting firmware
- Rely on third party tools and home grown tools
- Incorrect or attacked tools leave vulnerabilities
- Threats
- Disabled signing, for example
- Known attacks
- See e.g. Reflections on Trust, Ken Thompson**
- Mitigation
- Difficult: For most tools, provided as source code
- Review for correct implementation
- Use static, dynamic code analysis tools
- PyLint for Python, for example




+++?image=/assets/images/slides/Slide72.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[We don’t always get to  choose our Assets 04]
<p align="right"><span class="gold" ><b>We don’t always get to  choose our Assets</b></span></p>

Note:
- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 55  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 54-55 of PPT




#### BIOS Flash
- NIST SP800-147 says
- Lock code flash except for update before Exit Mfg Auth
- Signed update (>= RSA2048, SHA256)
- High quality signing servers
- Without back doors (“non-bypassability”)
- Threats
- PDOS – Permanent Denial of Service
- System into inefficient room heater
- Elevation of privilege
- Owning the system at boot is an advantage to a virus
- Known attacks
- CIH / Chernobyl 1999-2000
- Mebroni 2010
- Mitigations include
- Reexamining flash protection methods – use the best even if its new
- Using advanced techniques to locate and remove (un)intentional backdoors

#### SMM is valuable because
- It’s invisible to Anti Virus, etc
- SMM sees all of system RAM
- Not too different from PCI adapter device firmware
- Threats
- Elevation
- View secrets or own the system by subverting RAM
- Known attacks
- See e.g Duflot, Legbacore
- Mitigations include
- Validate “external” / “untrusted” input
- Remove calls from inside SMM to outside SMM

#### BOOT FLOW
- Secure boot
- Authenticated variables
- Based on the fundamental Crypto being correct
- Correct location for config data
- Threats
- Run unauthorized op roms, boot loaders
- PDOS systems with bad config variables
- Known attacks
- Mitigations include
- Sanity check config vars before use, use defaults
- Reviews, fuzz checking, third party reviews, etc.

####RESUME From S3
- ACPI says that we return the system to the S5S0 configuration at S3S0
- Must protect the data structures we record the cold boot config in
- Threats
- Changing data structures could cause security settings to be incorrectly configured leaving S3
- Reopen the other assets’ mitigated threats 
- Known attacks
- Mitigations include
- Store data in SMM -or-
- Store hash of data structures and refuse to resume if the hashes don’t compare

#### BUILD TOOLS
- Tools create the resulting firmware
- Rely on third party tools and home grown tools
- Incorrect or attacked tools leave vulnerabilities
- Threats
- Disabled signing, for example
- Known attacks
- See e.g. Reflections on Trust, Ken Thompson**
- Mitigation
- Difficult: For most tools, provided as source code
- Review for correct implementation
- Use static, dynamic code analysis tools
- PyLint for Python, for example




+++?image=/assets/images/slides/Slide73.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[We don’t always get to  choose our Assets 05]
<p align="right"><span class="gold" ><b>We don’t always get to  choose our Assets</b></span></p>

Note:
- https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 55  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 54-55 of PPT




#### BIOS Flash
- NIST SP800-147 says
- Lock code flash except for update before Exit Mfg Auth
- Signed update (>= RSA2048, SHA256)
- High quality signing servers
- Without back doors (“non-bypassability”)
- Threats
- PDOS – Permanent Denial of Service
- System into inefficient room heater
- Elevation of privilege
- Owning the system at boot is an advantage to a virus
- Known attacks
- CIH / Chernobyl 1999-2000
- Mebroni 2010
- Mitigations include
- Reexamining flash protection methods – use the best even if its new
- Using advanced techniques to locate and remove (un)intentional backdoors

#### SMM is valuable because
- It’s invisible to Anti Virus, etc
- SMM sees all of system RAM
- Not too different from PCI adapter device firmware
- Threats
- Elevation
- View secrets or own the system by subverting RAM
- Known attacks
- See e.g Duflot, Legbacore
- Mitigations include
- Validate “external” / “untrusted” input
- Remove calls from inside SMM to outside SMM

#### BOOT FLOW
- Secure boot
- Authenticated variables
- Based on the fundamental Crypto being correct
- Correct location for config data
- Threats
- Run unauthorized op roms, boot loaders
- PDOS systems with bad config variables
- Known attacks
- Mitigations include
- Sanity check config vars before use, use defaults
- Reviews, fuzz checking, third party reviews, etc.

####RESUME From S3
- ACPI says that we return the system to the S5S0 configuration at S3S0
- Must protect the data structures we record the cold boot config in
- Threats
- Changing data structures could cause security settings to be incorrectly configured leaving S3
- Reopen the other assets’ mitigated threats 
- Known attacks
- Mitigations include
- Store data in SMM -or-
- Store hash of data structures and refuse to resume if the hashes don’t compare

#### BUILD TOOLS
- Tools create the resulting firmware
- Rely on third party tools and home grown tools
- Incorrect or attacked tools leave vulnerabilities
- Threats
- Disabled signing, for example
- Known attacks
- See e.g. Reflections on Trust, Ken Thompson**
- Mitigation
- Difficult: For most tools, provided as source code
- Review for correct implementation
- Use static, dynamic code analysis tools
- PyLint for Python, for example


---?image=/assets/images/slides/Slide41_1.JPG
@title[Baseline: Boot trust regions]
<p align="right"><span class="gold" >@size[1.1em](<b>Baseline: Boot trust regions</b>)</span></p>
@snap[north-west span-30]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.8em" ><br>
A Threat Model (TM) defines the security assertions and constraints for a product<br><br>
@size[.8em](&nbsp;&nbsp;&bull;&nbsp;Assets  )<br>
@size[.8em](&nbsp;&nbsp;&bull;&nbsp;Threats  )<br>
@size[.8em](&nbsp;&nbsp;&bull;&nbsp;Mitigations  )<br>
</span></p>
@snapend

Note:
- Left:  https://firmware.intel.com/blog/security-technologies-and-minnowboard-max?page=1 
- UEFI open platforms_Vincent.ppt slide 55  - CanSecWest 2015 -  Refrences [6]: reference # [6] Slide 54-55 of PPT

- Right:  https://soco.intel.com/docs/DOC-2298751  page 4 


#### Bullet Points
- A Threat Model (TM) defines the security assertions and constraints for a product
- Assets: What we’re protecting
- Threats: What we’re protecting it against
- Mitigations: How we’re protecting our Assets

- Use TM to narrow subsequent mitigation efforts
- Don’t secure review, fuzz test all interfaces
- Select the ones that are critical
- TM is part science, part art, part experience, part nuance, part preference
- Few big assets vs lots of focused assets


---
@title[Threat Model with Examples]
<p align="right"><span class="gold" ><b>Threat Model with Examples</b></span></p>

@snap[north span-100 ]
<br>
<br>
<table id="recTable">
	<tr>
		<td align="left" bgcolor="#0070C0" height=".0005"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Asset </b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0005"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Example Threats </b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0005"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Mitigations </b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0005"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Checks </b></span></p></td>
	</tr>
	<tr>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.45em" >Fimware/BIOS Flash Contents </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >CIH attack: erase Boot block </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >SPI locks, descriptor </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >CHIPSEC </span></p></td>
	</tr>
	<tr>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.45em" >SMM </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >Callouts; Acess to SMM </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >TSEG, SMRR, SMM_CODE_CHK </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >CHIPSEC </span></p></td>
	</tr>
	<tr>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.45em" >Execution Duritng Boot Flow </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >Run malware in OP ROM  </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >Secure Boot, DMA protection  </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >Manual testing -CHIPSEC </span></p></td>
	</tr>
	<tr>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:030%"><span style="font-size:0.45em" >S3 Boot Script & S3 Resume Boot Flow </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >Resume reconifiguration losing locks </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >SMM Lock Box </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >Manual testing -CHIPSEC </span></p></td>
	</tr>
	<tr>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:030%"><span style="font-size:0.45em" >UEFI Variables (includes Authenticated) </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >Variable store full; Content change </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >Atributes, Lock Protocol </span></p></td>
		<td align="left" bgcolor="#404040" height=".0005"><p style="line-height:025%"><span style="font-size:0.35em" >Manual testing -CHIPSEC </span></p></td>
	</tr>
	<tr>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >ETC &nbsp;.&nbsp;.&nbsp;. </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >&nbsp;</span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >&nbsp; </span></p></td>
		<td align="left" bgcolor="#0d0d0d" height=".0005"><p style="line-height:010%"><span style="font-size:0.35em" >&nbsp; </span></p></td>
	</tr>
</table>
@snapend

Note:
ETC ... scrolled off the bottom

---
@title[Summary - Platform Firmware Security – Why is it important? - boot flow]
<p align="right"><span class="gold" >@size[1.1em](<b>Summary <br></b>)<b>Platform Firmware Security – Why is it important?</b></span></p>
@snap[north-west span-45]
<br>
<br>
<br>
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Why is platform firmware Security important<br>&nbsp;</span></p>)
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">UEFI Boot flow with the threat model<br><br>&nbsp;</span></p>)
@snapend

@snap[north span-20 ]
<br>
<br>
<br>
<p style="line-height:60%"><span style="font-size:01.25em">@fa[arrow-right gp-bullet-ltgreen]<br><br><br>
@fa[arrow-right gp-bullet-ltgreen]<br>
&nbsp;</span></p>
@snapend

@snap[north-east span-45 ]
<br>
<br>
<br>
@box[bg-royal text-white rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Prevent low level attacks that could "brick" the system<br>&nbsp;</span></p>)
@box[bg-royal text-white rounded my-box-pad2 fragment ](<p style="line-height:40%"><span style="font-size:0.6em">Identify where UEFI FW is vulnerable &amp; define Threat Model<br>&nbsp;</span></p>)
@snapend



Note:
- Identify the Firmware Assets and where they are vulnerable, 
- Define a threat model
- With a list of assets , threats and mitigations





