
@title[UEFI boot flow with the threat model]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI boot flow</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI boot flow with the threat model</span>

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




---?image=/assets/images/slides/Slide55.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Execution Flow]
<p align="right"><span class="gold" ><b>UEFI Boot Execution Flow</b></span></p>

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



+++?image=/assets/images/slides/Slide56.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Execution Flow 02]
<p align="right"><span class="gold" ><b>UEFI Boot Execution Flow</b></span></p>

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


+++?image=/assets/images/slides/Slide57.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Execution Flow 03]
<p align="right"><span class="gold" ><b>UEFI Boot Execution Flow</b></span></p>

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



---?image=/assets/images/slides/Slide59.JPG
@title[UEFI & Platform Initialization Task Flow]
<p align="right"><span class="gold" ><b>UEFI & Platform Initialization Task Flow</b></span></p>

Note:

- S-CRTM is a ”static core root of trust for measurement.” The S-CRTM is the portion of the platform firmware that must be „implicitly trusted.‟ The S-CRTM makes the first measurements, starts TPM, and detects physical presence per the TCG privacy model.


---?image=/assets/images/slides/Slide61.JPG
@title[Firmware Attack Surfaces]
<p align="right"><span class="gold" ><b>Firmware Attack Surfaces</b></span></p>

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


---?image=/assets/images/slides/Slide63.JPG
@title[Goals of security architecture and assets that are protected ]
<p align="right"><span class="gold" ><b>Goals of security architecture and assets<br> that are protected </b></span></p>
<p align="right"><span style="font-size:0.5em" ><a href="http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf">NIST SP 800-33</a> – IT Security Objectives </span></p>

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

+++?image=/assets/images/slides/Slide64.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Goals of security architecture and assets that are protected  02]
<p align="right"><span class="gold" ><b>Goals of security architecture and assets<br> that are protected </b></span></p>
<p align="right"><span style="font-size:0.5em" ><a href="http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf">NIST SP 800-33</a> – IT Security Objectives </span></p>

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



+++?image=/assets/images/slides/Slide65.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Goals of security architecture and assets that are protected  03]
<p align="right"><span class="gold" ><b>Goals of security architecture and assets <br>that are protected </b></span></p>
<p align="right"><span style="font-size:0.5em" ><a href="http://csrc.nist.gov/publications/nistpubs/800-33/sp800-33.pdf">NIST SP 800-33</a> – IT Security Objectives </span></p>

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



---?image=/assets/images/slides/Slide67.JPG
@title[What to build & defend – Rationale for a threat model]
<p align="right"><span class="gold" ><b>What to build & defend <br> – Rationale for a threat model</b></span></p>

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


---?image=/assets/images/slides/Slide75.JPG
@title[Baseline: Boot trust regions]
<p align="right"><span class="gold" ><b>Baseline: Boot trust regions</b></span></p>

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


---?image=/assets/images/slides/Slide77.JPG
@title[Threat Model with Examples]
<p align="right"><span class="gold" ><b>Threat Model with Examples</b></span></p>

Note:


---?image=/assets/images/slides/Slide79.JPG
@title[Summary - Platform Firmware Security – Why is it important? - boot flow]
<p align="right"><span class="gold" ><b>Summary <br>Platform Firmware Security – Why is it important?</b></span></p>
<br>
<br>
<br>
<br>

Note:
- Identify the Firmware Assets and where they are vulnerable, 
- Define a threat model
- With a list of assets , threats and mitigations





