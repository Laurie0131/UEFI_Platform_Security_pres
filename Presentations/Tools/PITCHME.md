@title[Tools and resources  Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tools and resources </span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;How to test firmware for security  </span>

Note:
  SecurityTechnologies.md for UEFI / EDK II Training  Security technologies overview

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


---?image=assets/images/gitpitch-audience.jpg
@title[Automation Sub-section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Automation:</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Automated Test Generation Tools</span>


---?image=/assets/images/slides/Slide173.JPG
@title[Build a Security Mindset]
<p align="right"><span class="gold" >@size[1.1](<b>Build a Security Mindset</b>)</span></p>
<br>
<div class="left">
<br>
<span style="font-size:0.8em" >“Finding BIOS Vulnerabilities with Symbolic Execution and Virtual Platforms”: <a href="https://software.intel.com/en-us/blogs/2017/06/06/finding-bios-vulnerabilities-with-excite"> Excite Link</a></span>
</div>
<div class="right">
<span style="font-size:0.8em" >&nbsp;</span>
</div>

Note:
- We want to Build firmware with a  Security Mindset
- Finding vulnerabilities in code is part of the constant security game between attackers and defenders. An attacker only needs to find one opening to be successful, while a defender needs to search for and plug all or at least most of the holes in a system. 
- Thus, a defender needs more effective tools than the attacker to come out ahead.
- Tools like excite use Symbolic Execution to test for vulnerabilities.

- What if there was a tool to help us determine if the Platform Code is doing the right thing?
- As New attacks are discovered 
  - Research is done determining the root cause  of the attack
- Then a test could be done to test that a platform does not expose that vulnerability






---
@title[What is Excite?]
<p align="right"><span class="gold" >@size[1.1](<b>What is Excite?</b>)</span></p>
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><font color="yellow">Goal</font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" ><b><u>Automatically</u></b> detect security issues  in UEFI BIOS </span>  </li>
    <ul style="list-style-type:disc">
       <li><span style="font-size:0.65em" >Complement  other approaches: security code reviews, static analysis, Chipsec …</span>  </li>
    </ul>
  </ul>
  <li><span style="font-size:0.8em" ><font color="yellow">Aproach</font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Apply open source <b>fuzzing & symbolic execution</b> tools to Intel Architecture binaries</span>  </li>
  </ul>
  <li><span style="font-size:0.8em" ><font color="yellow">Versions</font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" ><b>Excite</b> : Symbolic Execution using CRETE and Simics</span>  </li>
    <li><span style="font-size:0.7em" ><b>Excite DBI </b>(Dynamic Binary Instrumentation): Fuzzing using AFL and Intel Pin Tool </span>  </li>
  </ul>
</ul>
<p style="line-height:40%"><span style="font-size:0.5em" >AFL - American Fuzzy Lop (fuzzer)<br>
 Pin – Intel tool to determine trace<br>
 CRETE -<a href="https://github.com/SVL-PSU/crete-dev"> github crete-dev</a> </span></p>
</ul>

@snap[south-east span-25]
![excite](/assets/images/Excite.png)
@snapend

Note:


- Firmware Summit slides
- What is Excite – Automated Test Generation

- Motivation
- Automatically detect BIOS SMI security issues  
- Eg.  SMRAM callouts and accesses of  invalid memory regions
- Complement  other approaches: security code reviews, static analysis, Chipsec …
- Approach
- Apply open source symbolic execution and fuzzing tools to x86 binaries
- Leverage Simics to run early in a platform’s development
- Start with  comm buffer based SMI handlers
- Extend to SMM drivers and other UEFI components

- The goal is to explore the BIOS – FW Code and Identify parts of the code that are manifesting security vulnerabilities 

- PIN – Intel tool that allows the trace of the execution of where the fuzzer is getting to in the BIOS Source code.  Lines of code hit – disassembly
- CRETE – Symbolic execution engine – open source from Portland State U. 

- Excite does NOT:
- Statically analyze C source code
- Validate platform security settings and configuration
- Replace security code reviews
- Cover all types of security issues


---
@title[What is Fuzzing?]
<p align="right"><span class="gold" >@size[1.1](<b>What is Fuzzing?</b>)</span></p>
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" >Technique of providing variety of invalid, unexpected, or random data as inputs to target code to try to make it misbehave </span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.8em" >Some inputs are non-intuitive, harder for developers to discover</span>  </li><br>
  </ul>
  <li><span style="font-size:0.9em" ><font color="yellow"><b>Why fuzz UEFI?</b></font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.8em" >Find security issues early</span>  </li>
    <ul style="list-style-type:disc">
     <li><span style="font-size:0.7em" >Complement manual code reviews</span>  </li>
     <li><span style="font-size:0.7em" >Re-run as software evolves</span>  </li>
    <li><span style="font-size:0.8em" >New vulnerability detection capability</span>  </li>
  </ul>
 </ul>

Note:
 
---?image=/assets/images/slides/Slide150.JPG
@title[Symbolic Execution  (S2E)– SMM Example]
<p align="right"><span class="gold" >@size[1.1](<b>Symbolic Execution  (S2E)– SMM Example</b>)</span></p>
<br>
<div class="left2">
<ul style="list-style-type:disc">
  <li><span style="font-size:0.8em" >Searching for SMM security vulnerabilities </span> </li>
  <li><span style="font-size:0.8em" >Symbolic execution generates test cases that cover the computation tree of the handler and induce vulnerabilities. </span> </li>
  <li><span style="font-size:0.8em" >Those test cases are replayed in Simics which detects illegal accesses and SMM callouts. (e.g. read memory outside SMRAM) </span> </li>
</ul>
<br>
<br>
<br>

<p style="line-height:40%"><span style="font-size:0.5em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Symbolic execution for BIOS security<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <a href="https://www.usenix.org/system/files/conference/woot15/woot15-paper-bazhaniuk.pdf">woot15-paper-bazhaniuk PDF </a> </span></p>
</div>
<div class="right2">
<span style="font-size:0.8em" > &nbsp;</span> 
</div>

Note: 
 
- Given a snapshot of SMRAM, the base address of SMRAM, and the address of the variable interrupt handler in SMRAM, the tool uses S2E to run the symbolic execution engine to search for concrete examples of a call to the SMI interrupt handler that causes the handler to read memory outside of SMRAM
  
 
---?image=/assets/images/slides/Slide91_1.JPG
@title[Excite - Common Flow]
<p align="right"><span class="gold" >@size[1.1](<b>Excite - Common Flow</b>)</span></p>

@snap[south-west span-100]
<p style="line-height:30%"><span style="font-size:0.4em" >
<sup>1.</sup>Selective Symbolic Execution ( S2E | CRETE)  <br>
<sup>2.</sup><a href="http://lcamtuf.coredump.cx/afl/">American Fuzzy Lop (fuzzier)</a>
</span></p>
@snapend

Note:
- On the slide you can see Excite flow. Currently it works almost automatically. Source tree of BIOS is downloaded from repository, and we build it.  Then the BIOS is executed either on a live system or using Simics
- Next step is dumping  a snap shot of SMRAM, memory maps and addresses of SMM handlers by Simics.  (Hardware debugger like ITP on live platform)

- Example of the memory snap shot – 
  - UEFI PE Module that resides in SMRAM
  - Intel SMI Transfer Module (STM) 
 - Purpose of the snapshot is to gather information about which memory regions are mapped to determine is memory access are done outside the correct region


- Further test harness is created, and we run selective symbolic execution engine for generation of test cases. (CRETE / AFL)
- We play it in simics generated by s2e tests and new tests produced by fuzzing, check security issues and measure code coverage.  
  - For example  finding SMRAM Call out security issues

- As output we have Security Issue and code coverage reports and set of test cases.

- AFL - http://lcamtuf.coredump.cx/afl/  


---
@title[Excite Benefits]
<p align="right"><span class="gold" >@size[1.1](<b>Excite Benefits</b>)</span></p>
<br>
<ul style="list-style-type:none">
  <li><span style="font-size:0.9em" ><b>Extend fuzzing beyond interface level </b></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.8em" >UEFI code (SMM, STM, UEFI PE modules) accessible to AFL/CRETE, Pin, gdb. </span>  </li>
    <li><span style="font-size:0.8em" >Record/analyze code flow, call trace, memory access data  </span>  </li>
    <li><span style="font-size:0.8em" >Individual functions accessible, new inputs created, can test different flows</span>  </li><br>
  </ul>
  <li><span style="font-size:0.9em" ><b>Quantify code coverage reporting </b></span>  </li>
</ul>
<br>
<br>
<br>
<span style="font-size:0.4em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Resource: <a href="https://firmware.intel.com/content/smi-transfer-monitor-stm ">STM-SMI Transfer Monitor </a></span>

@snap[south-east span-25]
![excite](/assets/images/Excite.png)
@snapend


Note:

- One of the key benefits of EXCITE is previously there has been fuzzing done at the interface level

- EXICTE Extends fuzzing BEYOND the interface level by
- Stepping into specific modules and begin to FUZZ those working at a more granular bases 
  - For example:  Stepping into the UEFI code (SMM, STM, UEFI PE modules) that is accessible to AFL/CRETE, Pin, gdb. 

- We also get very detailed information about call traces - memory access data – the code flow 
- And then we can interact with these snap shots in different ways
    - For example: we can construct different flows and analyze that.  
      - we can dump and modify variables / UEFI PCD

- We can access Individual functions , new inputs created and can test different flows

- Also creates Quantify code coverage reports

##### CHALLENGES
- Scalability (privileged instructions, function coverage) ring3 – ring0
- Simplification for broader deployment
- Performance of engine  - fuzzing is slow 
- Could accelerate with parallelization

- Road Map
- Add more automation/reporting features to reduce user time
- Broaden scale of code to be tested
- Consolidate approaches
- Open-source? TBD


---?image=assets/images/gitpitch-audience.jpg
@title[Known Issue  Sub-section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Known Issue :</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tools for Testing Known Issue </span>
  
---
@title[Raising the Bar for Platform Security]
<p align="center"><span class="gold" >@size[1.1](<b>Raising the Bar for Platform Security</b>)</span></p>
@snap[north-east span-10 ]
![chipsec-logo](/assets/images/chipsec_logo.png)
</span></p>

@snapend


@snap[north-west span-30 fragment]
<br>
<br>
<br>
![NewAttacks](/assets/images/NewAttacks.png)
</span></p>
@snapend

@snap[north span-30 fragment]
<br>
<br>

<p style="line-height:30%"><span style="font-size:0.4em" ><br><br>
</span></p>

![TestModules](/assets/images/TestModules.png)
</span></p>
@snapend

@snap[north-east span-25 fragment]
<br>
<br>
<br>
<p style="line-height:30%"><span style="font-size:0.4em" ><br><br>
</span></p>

![Riskprofile](/assets/images/Riskprofile.png)
</span></p>
@snapend

@snap[south-west span-100 fragment]
<p style="line-height:80%"><span style="font-size:0.95em" ><b>
Empowering End-Users to Make a Risk Decision</b><br><br>
</span></p>
<br>
@snapend

@snap[south-west span-100]
<p style="line-height:30%"><span style="font-size:0.4em" >
Source: <a href="https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf">CHIPSEC-csw14 PDF </a>
</span></p>
@snapend
 

Note:
- Source: https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf

- What if there was a tool to help us determine if the Platform Code is doing the right thing?

- As New attacks are discovered 
  - Research is done determining the root cause  of the attack

- Then a test could be done to test that a platform does not expose that vulnerability

- Introducing CHIPSEC

 
---?image=/assets/images/slides/Slide95_1.JPG
@title[What is CHIPSEC?]
<p align="center"><span class="gold" >@size[1.1](<b>What is CHIPSEC?</b>)</span></p>
<div class="left2">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><font color="yellow"><b>Framework for Platform Security Assessment</b></font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Tests for known security issues</span>  </li>
    <li><span style="font-size:0.7em" >Tools for investigation of platform properties</span>  </li><br>
  </ul>
  <li><span style="font-size:0.8em" ><font color="yellow"><b>Open Source (GPLv2 License)</b></font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Released in 2014 – @fa[github gp-bullet-white]<span style="font-size:0.7em">&nbsp;<a href="https://github.com/chipsec/chipsec "> https://github.com/chipsec/chipsec </a></span></span>  </li>
    <li><span style="font-size:0.7em" >Currently active community</span>  </li><br>
    <li><p style="line-height:40%"><span style="font-size:0.7em" >Top referring sites: </span><span style="font-size:0.6em" >Google, Github, <a href="">pcworld.com</a>, 
	<a href="">community.spiceworks.com</a>,
	<a href="">anonhq.com</a>, Twitter, <a href="">securingtomorrow.mcafee.com</a>,
	<a href="">intelsecurity.com</a>,
	<a href="">cylance.com</a></span> </p> </li>
  </ul>
</ul>
</div>
<div class="right2">
<span style="font-size:0.8em" > &nbsp;</span> 
</div>
Note:
- What is Chipsec – KNOWN Issue testing
- Designed to look for platform Miss-configurations

- Think about how MSR and the Chipset is programed,  CHIPSEC can look for known miss- configurations and make a report 

 

---?image=/assets/images/slides/SlideChipSec_logo.JPG
@title[Chipsec Framework overview]
<p align="center"><span class="gold" >@size[1.1](<b>Chipsec Framework overview</b>)</span></p>

@snap[north span-85]
<br>
<br>
<br>
![Chipsec_diagram](/assets/images/Chipsec_diagram.png)
@snapend

@snap[south-west span-100]
<p style="line-height:30%"><span style="font-size:0.4em" >
Source: <a href="https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf">Cansecwest 2014</a>
</span></p>

@snapend

Note:


 
---?image=/assets/images/slides/SlideChipSec_logo.JPG
@title[Example Chipsec Check - SPI Controller LOCK]
<br>
<p align="center"><span class="gold" >@size[1.1](<b>Example Chipsec Check - SPI Controller LOCK</b>)</span></p>
<br>
<ul style="list-style-type:disc">
  <li><span style="font-size:0.8em" ><font color="cyan">FLOCKDN – Reg that Locks critical SPI controller registers</font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Flash Region Access Permissions</span>  </li>
    <li><span style="font-size:0.7em" >Secondary Flash Region Access Permissions</span>  </li>
    <li><span style="font-size:0.7em" >Flash Protected Range Registers</span>  </li>
    <li><span style="font-size:0.7em" >Other Settings</span>  </li>
  </ul>
  <li><span style="font-size:0.8em" ><font color="cyan">Without setting this bit some SPI protections may be modified or bypassed</font></span>  </li>
  <li><span style="font-size:0.8em" ><font color="cyan">Chipsec provides the `common.spi_lock` test to verify this setting</font></span>  </li>
</ul>
<br>
<span style="font-size:0.5em" >FLOCKDN – Flash Configuration Lock down Reg </span>

Note:


- AS an Example of something CHIPSEC can test.

- Think about your FLASH or SPI controller – if an attacker is going to attack through the SPI Part 
  – they would be able to inject code  and directly write to the Flash  their own code that could then be loaded upon re-boot  thus Root Kitting your system.

- CHIPSEC can test for if these flash regions are exposed to write to.

- For example FLOCKDN – Lock down REG that Locks critical SPI controller registers


---?image=/assets/images/slides/SlideChipSec_logo.JPG
@title[Sample Issue Discovered]
<br>
<p align="center"><span class="gold" >@size[1.1](<b>Sample Issue Discovered</b>)</span></p>
<span style="font-size:01.0em" ><font color="cyan">Is BIOS correctly protected?</font></span>
<br>
```
[*] running module: chipsec.modules.common.spi_lock
[x][ =======================================================================
[x][ Module: SPI Flash Controller Configuration Lock
[x][ =======================================================================
[*] HSFS = 0x6008 << Hardware Sequencing Flash Status Register (SPIBAR + 0x4)
    [00] FDONE            = 0 << Flash Cycle Done
    [01] FCERR            = 0 << Flash Cycle Error
    [02] AEL              = 0 << Access Error Log
    [03] BERASE           = 1 << Block/Sector Erase Size
    [05] SCIP             = 0 << SPI cycle in progress
    [13] FDOPSS           = 1 << Flash Descriptor Override Pin-Strap Status
    [14] FDV              = 1 << Flash Descriptor Valid
    [15] FLOCKDN          = 0 << Flash Configuration Lock-Down
	[-] FAILED: SPI Flash Controller configuration is not locked
```
<span style="background-color: #101010"><span style="font-size:0.6em" ><font color="red">`[-] FAILED: SPI Flash Controller configuration is not locked`</font></span></span><br>

Note:
- The CHIPSEC Test chipsec.modules.common.spi_lock

- Shows this report showing that the FLOCKND bit is NOT set thus the SPI Flash Controller is not locked

- There are many other tests


---?image=/assets/images/slides/SlideChipSec_logo2.JPG
@title[Known Threats and Chipsec modules]
<p align="center"><span class="gold" >@size[1.1](<b>Known Threats and Chipsec modules</b>)</span></p>

<table id="recTable">
	<tr>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>Issue</span></b></td>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>CHIPSEC Module</b></span></td>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>References</b></span></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><span style="font-size:0.56em" >SMRAM Locking &nbsp;</span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >common.smm&nbsp;</span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" ><a href="http://www.ssi.gouv.fr/archive/fr/sciences/fichiers/lti/cansecwest2006-duflot.pdf">CanSecWest 2006</a>&nbsp;</span></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >BIOS Keyboard Buffer Sanitization </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_kbrd_buffer </span></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" ><a href="http://www.slideshare.net/endrazine/defcon-16-bypassing-preboot-authentication-passwords-by-instrumenting-the-bios-keyboard-buffer-practical-low-level-attacks-against-x86-preboot-authentication-software">DEFCON 16 </a> </span></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >SMRR Configuration </span></p></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >common.smrr </span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" ><a href="http://www.invisiblethingslab.com/resources/misc09/smm_cache_fun.pdf">ITL 2009 </a> , 
		<a href="http://cansecwest.com/csw09/csw09-duflot.pdf">CanSecWest 2009 </a> </span></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><span style="font-size:0.56em" >BIOS Protection </span></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_wp </span></td>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://www.blackhat.com/presentations/bh-usa-09/WOJTCZUK/BHUSA09-Wojtczuk-AtkIntelBios-SLIDES.pdf">BlackHat USA 2009 </a>,  
		<a href="https://www.blackhat.com/us-13/briefings.html">CanSecWest 2013 </a>, 
		<a href="https://www.blackhat.com/us-13/briefings.html">Black Hat 2013 </a>, 
		<a href="http://www.nosuchcon.org/talks/D2_01_Butterworth_BIOS_Chronomancy.pdf">NoSuchCon 2013 </a>, </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >SPI Controller Locking </span></p></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >common.spi_lock </span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" ><a href="http://www.flashrom.org/">Flashrom </a>, 
		<a href="http://www.mitre.org/capabilities/cybersecurity/overview/cybersecurity-blog/copernicus-question-your-assumptions-about">Copernicus </a> </span></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >BIOS Interface Locking </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_ts </span></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" ><a href="http://powerofcommunity.net/poc2007/sunbing.pdf">PoC 2007 </a> </span></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >Secure Boot variables with keys and configuration are protected </span></p></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >common.secureboot.variables </span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://uefi.org/">UEFI 2.4 Spec  </a>,
		  All Your Boot Are Belong To Us ( <a href="https://cansecwest.com/slides/2014/AllYourBoot_csw14-intel-final.pdf">here </a> & 
		  <a href="https://cansecwest.com/slides/2014/AllYourBoot_csw14-mitre-final.pdf">here </a>) </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >Memory remapping attack </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >remap </span></td>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://www.invisiblethingslab.com/resources/bh08/part2-full.pdf">Preventing and Detecting Xen Hypervisor Subversions </a> </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >DMA attack against SMRAM </span></p></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >smm_dma </span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://www.ssi.gouv.fr/archive/fr/sciences/fichiers/lti/pacsec2007-duflot-papier.pdf">Programmed I/O accesses: a threat to VMM? </a>, 
		<a href="http://www.ssi.gouv.fr/uploads/IMG/pdf/IT_Defense_2010_final.pdf">System Management Mode Design and Security Issues </a></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >SMI suppression attack </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_smi </span></td>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="https://www.hackinparis.com/sites/hackinparis.com/files/JohnButterworth.pdf">Setup for Failure: Defeating Secure Boot </a> </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><span style="font-size:0.56em" >ETC . . .   </span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" > </span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >See <a href="https://github.com/chipsec/chipsec">https://github.com/chipsec/chipsec </a> </span></p></td>
	</tr>
</table>

Note:
Source: https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf


+++?image=/assets/images/slides/SlideChipSec_logo2.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Known Threats and Chipsec modules 02]
<p align="center"><span class="gold" >@size[1.1](<b>Known Threats and Chipsec modules</b>)</span></p>

<table id="recTable">
	<tr>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>Issue</span></b></td>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>CHIPSEC Module</b></span></td>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>References</b></span></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >BIOS Interface Locking </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_ts </span></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" ><a href="http://powerofcommunity.net/poc2007/sunbing.pdf">PoC 2007 </a> </span></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >Secure Boot variables with keys and configuration are protected </span></p></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >common.secureboot.variables </span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://uefi.org/">UEFI 2.4 Spec  </a>,
		  All Your Boot Are Belong To Us ( <a href="https://cansecwest.com/slides/2014/AllYourBoot_csw14-intel-final.pdf">here </a> & 
		  <a href="https://cansecwest.com/slides/2014/AllYourBoot_csw14-mitre-final.pdf">here </a>) </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >Memory remapping attack </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >remap </span></td>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://www.invisiblethingslab.com/resources/bh08/part2-full.pdf">Preventing and Detecting Xen Hypervisor Subversions </a> </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >DMA attack against SMRAM </span></p></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >smm_dma </span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="http://www.ssi.gouv.fr/archive/fr/sciences/fichiers/lti/pacsec2007-duflot-papier.pdf">Programmed I/O accesses: a threat to VMM? </a>, 
		<a href="http://www.ssi.gouv.fr/uploads/IMG/pdf/IT_Defense_2010_final.pdf">System Management Mode Design and Security Issues </a></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >SMI suppression attack </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_smi </span></td>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="https://www.hackinparis.com/sites/hackinparis.com/files/JohnButterworth.pdf">Setup for Failure: Defeating Secure Boot </a> </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><span style="font-size:0.56em" >ETC . . .   </span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" > </span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >See <a href="https://github.com/chipsec/chipsec">https://github.com/chipsec/chipsec </a> </span></p></td>
	</tr>

</table>

Note:

+++?image=/assets/images/slides/SlideChipSec_logo2.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Known Threats and Chipsec modules 03]
<p align="center"><span class="gold" >@size[1.1](<b>Known Threats and Chipsec modules</b>)</span></p>

<table id="recTable">
	<tr>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>Issue</span></b></td>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>CHIPSEC Module</b></span></td>
		<td bgcolor="#0071c5"><span style="font-size:0.75em" ><b>References</b></span></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" >SMI suppression<br> attack </span></p></td>
		<td bgcolor="#323232"><span style="font-size:0.56em" >common.bios_smi </span></td>
		<td bgcolor="#323232"><p style="line-height:40%"><span style="font-size:0.56em" ><a href="https://www.hackinparis.com/sites/hackinparis.com/files/JohnButterworth.pdf">Setup for Failure: <br>Defeating Secure Boot </a> </span></p></td>
	</tr>
	<tr>
		<td bgcolor="#121212"><span style="font-size:0.56em" >ETC . . .   </span></td>
		<td bgcolor="#121212"><span style="font-size:0.56em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></td>
		<td bgcolor="#121212"><p style="line-height:40%"><span style="font-size:0.56em" >See <a href="https://github.com/chipsec/chipsec">github.com/chipsec/ </a> </span></p></td>
	</tr>

</table>

Note:


---?image=/assets/images/slides/SlideChipSec_logo2.JPG
@title[CHIPSEC Modules ]
<br>
<p align="center"><span class="gold" >@size[1.1](<b>CHIPSEC Modules </b>)</span></p>
<span style="font-size:0.9em" >Modules encapsulate the main functionality of CHIPSEC:</span> 
<ol>
  <li><span style="font-size:0.8em" >Tests for known vulnerabilities in firmware</span>  </li>
  <li><span style="font-size:0.8em" >Tests for insufficient or incorrectly configured hardware protections</span>  </li>
  <li><span style="font-size:0.8em" >Hardware/firmware-level security tools</span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Fuzzing tools for firmware interfaces/formats</span>  </li>
    <li><span style="font-size:0.7em" >Manual security checkers (e.g. TE checker, DMA dumper)</span>  </li>
    <li><span style="font-size:0.7em" >Reside in `modules/tools` directory are not launched automatically (only through –m command-line option)</span>  </li>
  <li><span style="font-size:0.8em" >PoC exploit modules demonstrating vulnerabilities</span>  </li>
<ol>

Note:

Here are some more Details about CHIPSEC


---?image=/assets/images/slides/SlideChipSec_logo2.JPG
@title[CHIPSEC Modules ]
<br>
<p align="center"><span class="gold" >@size[1.1](<b>CHIPSEC Modules </b>)</span></p>
<br>
<ul>
  <li><span style="font-size:0.8em" >All modules reside in `chipsec/modules` directory</span>  </li>
  <li><span style="font-size:0.8em" >Modules can be specific to one or more platforms or common for all supported platforms</span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Modules in `modules/<platform_code>` directory will only be executed on `<platform_code>` platform </span>  </li>
    <li><span style="font-size:0.7em" >Modules in `modules/common` directory will always be executed </span>  </li>
  </ul>
  <li><span style="font-size:0.8em" >Modules can implement is_supported function which can further check for supported platforms, OS environments (legacy vs. UEFI boot), etc.</span>  </li>
</ul>
  

Note:



---?image=assets/images/gitpitch-audience.jpg
@title[HBFA  Sub-section]
<br><br><br><br><br><br><br>
<p style="line-height:80%"><span style="font-size:01.1em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#e49436">Shift-Left Firmware Security Testing :</font></span></p>
<span style="font-size:0.9em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Host-based Firmware Analyzer (HBFA) </span>
  
---
@title[Common Tools for Firmware Security Testing]
<p align="right"><span class="gold" >@size[1.1](<b>Common Tools for Firmware Security Testing</b>)</span></p>

<p style="line-height:80%"><span style="font-size:0.9em" ><br>
<a href="">CHIPSEC</a>: open source framework for analyzing the security of platform firmware and hardware configuration at runtime, based on the 
Unified Extensible Firmware Interface (<a href="">UEFI</a>) specification.
<br><br>
<a href="https://software.intel.com/en-us/blogs/2017/06/06/finding-bios-vulnerabilities-with-excite">Symbolic Execution and Virtual Platforms: Excite</a> project on Intel uses a combination of symbolic execution, fuzzing, and concrete testing to find 
vulnerabilities in firmware running on Wind River* <a href="https://software.intel.com/en-us/blogs/2017/06/06/finding-bios-vulnerabilities-with-excite">Simics</a> virtual platforms.
</span></p>
<p style="line-height:70%"><span style="font-size:0.8em" ><br>
<font color="yellow"><i>
Great tools… but they’re based on integration testing, so issues are more expensive to detect and mitigate. 
<u>Can we improve testing before integration?</u>
</i></font>
</span></p>

Note:

 
---?image=/assets/images/slides/Slide106_1.JPG
@title[Shift Left – Design for Security Test (DFST)]
<p align="right"><span class="gold" >@size[1.1](<b>Shift Left – Design for Security Test (DFST)</b>)</span></p>

@snap[south span-85 fragment]
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.8em">How can we improve security test efficiency?<br>&nbsp;</span></p>)
@snapend


Note:

As testing moves toward the release there is an increase to the cost

How can we improve security test efficiency?

---
@title[Design for Security Test (DFST)]
<p align="right"><span class="gold" >@size[1.1](<b>Design for Security Test (DFST)</b>)</span></p>
<br>

<p style="line-height:80%"><span style="font-size:0.9em" ><br><br>
<i>&quot;Engineers should recognize that reducing risk is not an impossible task, even under financial and time constrains.<br><br>
All it takes in many cases is a different perspective on the design problem.&quot;</i>
</span></p>
<p style="line-height:80%" align="right"><span style="font-size:0.7em" >
  &hyphen;&hyphen; Mike Martin & Roland Schinizinger&nbsp;&nbsp;&nbsp;
</span></p>


---?image=/assets/images/slides/Slide108_1.JPG
@title[Host-based Firmware Analyzer]
<p align="right"><span class="gold" >@size[1.1](<b>Host-based Firmware Analyzer</b>)</span></p>

<p style="line-height:80%"><span style="font-size:0.9em" ><br>
Test for BIOS code under OS:  Pure software logic
</span></p>

@snap[north span-85 fragment]
<br>
<br>
<br>
<br>
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.8em">Benefit: @color[yellow](30X) faster than UEFI based running env(OVMF).<br>&nbsp;</span></p>)
@snapend

Note:

---
@title[Host-based Firmware Analyzer Architecture]
<p align="right"><span class="gold" >@size[1.1](<b>Host-based Firmware Analyzer Architecture</b>)</span></p>

@snap[north span-85 ]
<br>
<br>
<br>
![HBFA_FW](/assets/images/HostBasedFW_test.png)
@snapend

@snap[south span-90 fragment]
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:85%"><span style="font-size:0.8em">Implementing  testing UEFI Firmware under OS environment <br>&nbsp;</span></p>)
@snapend

Note:


---?image=/assets/images/slides/Slide110_1.JPG
@title[Host-based Firmware Analyzer]
<p align="right"><span class="gold" >@size[1.1](<b>Host-based Firmware Analyzer</b>)</span></p>

<p style="line-height:80%"><span style="font-size:0.9em" >
<font color="cyan"><i>OS based environment utilizing best-in-class test tools</i></font>
</span></p>

@snap[north-west span-55]
<br>
<br>
<br>
<br>

<ul style="list-style-type:none; line-height:0.7;">
  <li><span style="font-size:0.65em" >GUI and command-line interfaces	 <br> &nbsp;</span> </li>
  <li><span style="font-size:0.65em" >Fuzzing testing (AFL, libFuzzer, Peach)		<br>&nbsp;  </span> </li>
  <li><span style="font-size:0.65em" >Symbolic execution (KLEE/STP)		<br>&nbsp;  </span> </li>
  <li><span style="font-size:0.65em" >Address Sanitizer & Code Coverage		 <br>&nbsp; </span> </li>
  <li><span style="font-size:0.65em" >Automated unit test execution	 <br>&nbsp; </span> </li>
  <li><span style="font-size:0.65em" >Instrumentation methods for fault injection and trace	 <br>&nbsp; </span> </li>
  <li><span style="font-size:0.65em" >FDatabase of unit test cases		<br>&nbsp;  </span> </li>
</ul>
@snapend

---
@title[Host-based Firmware Analyzer summary]
<p align="right"><span class="gold" >@size[1.1](<b>HBFA - Summary</b>)</span></p>
<p style="line-height:80%"><span style="font-size:0.9em" ><br>
<font color="cyan">Host Based Firmware Analyzer (HBFA)</font>
</span></p>
<ul style="list-style-type:disc; line-height:0.8;">
  <li><span style="font-size:0.7em" >Isolate test environment – run test under OS (like OS application)		  </span> </li>
  <li><span style="font-size:0.7em" >Integrate with OS based fuzz/Symbolic tool, such as AFL, KLEE, Peach.		  </span> </li>
  <li><span style="font-size:0.7em" >Provide an infrastructure to build Pure Software Logic function of BIOS.		  </span> </li>
</ul>

<p style="line-height:80%"><span style="font-size:0.9em" >
<font color="cyan">Benefit</font> - Make it Easy for
</span></p>
<ul style="list-style-type:disc; line-height:0.8;">
  <li><span style="font-size:0.7em" >Secure Fuzzy Test.		  </span> </li>
  <li><span style="font-size:0.7em" >Test automation and case reuse.		  </span> </li>
  <li><span style="font-size:0.7em" >Code Coverage , debugging with OS Debugger tool		  </span> </li>
</ul>


---
@title[Host-based Firmware Analyzer Expectation]
<p align="right"><span class="gold" >@size[1.1](<b>Expectation</b>)</span></p>
<p style="line-height:80%"><span style="font-size:0.9em" ><br>
<b>Developer:</b>
</span></p>
<ul style="list-style-type:disc; line-height:0.7;">
  <li><span style="font-size:0.7em" >Easily enable fuzz test in unit test Phase.  </span> </li>
</ul>

<p style="line-height:80%"><span style="font-size:0.9em" >
<b>Benefit</b>
</span></p>
<ul style="list-style-type:disc; line-height:0.8;">
  <li><span style="font-size:0.7em" >Reduce the total cost of a project. </span> </li>
  <li><span style="font-size:0.7em" >Help to detect and fix security issue quickly  </span> </li>
  <li><span style="font-size:0.7em" >QA can focus on other security test. (eg, system level or cost much time to set up env)  </span> </li>
</ul>

<p style="line-height:70%"><span style="font-size:0.7em" >
Release on <a href="https://www.tianocore.org">tianocore.org</a> wiki page for <a href="https://github.com/tianocore/tianocore.github.io/wiki/Host-Based-Firmware-Analyzer"> Host Based Firmware Analyzer(HBFA)</a>
</span></p>

---?image=/assets/images/slides/Slide104_1.JPG
@title[EDK II Security White Paper list ]
<p align="right"><span class="gold" >@size[1.1](<b>EDK II Security White Paper list </b>)</span></p>


@snap[north-west span-45]
<br>
<br>
<br>
<p style="line-height:95%"><span style="font-size:0.9em" >
List of helpful links and white papers based on Security with EDK II on wiki page: <a href="https://github.com/tianocore/tianocore.github.io/wiki/EDK-II-Security-White-Papers">Edk II Security White Papers</a>
</span></p>
@snapend

---
@title[Summary - Platform Firmware Security – Why is it important? - boot flow]
<p align="right"><span class="gold" >@size[1.1em](<b>Summary <br></b>)<b>Platform Firmware Security – Why is it important?</b></span></p>
@snap[north-west span-45]
<br>
<br>
<br>
@box[bg-purple-pp text-gray rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Why is platform firmware Security important<br>&nbsp;</span></p>)
@box[bg-purple-pp text-gray rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">UEFI Boot flow with the threat model<br><br>&nbsp;</span></p>)
@box[bg-purple-pp text-gray rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Security technologies overview<br><br><br>&nbsp;</span></p>)
@snapend

@snap[north span-20 ]
<br>
<br>
<br>
<p style="line-height:60%"><span style="font-size:01.25em">@fa[arrow-right gp-bullet-ltgreen]<br><br><br>
@fa[arrow-right gp-bullet-ltgreen]<br><br><br>
@fa[arrow-right gp-bullet-ltgreen]<br><br><br>
&nbsp;</span></p>
@snapend

@snap[north-east span-45 ]
<br>
<br>
<br>
@box[bg-royal text-gray rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Prevent low level attacks that could "brick" the system<br>&nbsp;</span></p>)
@box[bg-royal text-gray rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Identify where UEFI FW is vulnerable &amp; define Threat Model<br>&nbsp;</span></p>)
@box[bg-royal text-gray rounded my-box-pad2 ](<p style="line-height:40%"><span style="font-size:0.6em">Boot Guard, Secure Boot and NIST Secure Updates provide mitigations to some hacking methods <br>&nbsp;</span></p>)

@snapend

@snap[north-west span-45 fragment]
<br>
<br>
<br>
<p style="line-height:40%"><span style="font-size:0.6em"><br><br><br>&nbsp;</span></p>
<p style="line-height:40%"><span style="font-size:0.6em"><br><br><br>&nbsp;</span></p>
<p style="line-height:40%"><span style="font-size:0.6em"><br><br><br>&nbsp;</span></p>
@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:40%"><span style="font-size:0.6em">Tools and resources on how to test firmware for security<br><br>&nbsp;</span></p>)
@snapend

@snap[north span-20  fragment]
<br>
<br>
<br>
<br>
<p style="line-height:60%"><span style="font-size:01.25em">&nbsp;<br><br><br>
&nbsp;<br><br><br>
&nbsp;<br><br><br><br>
@fa[arrow-right gp-bullet-ltgreen]<br>
&nbsp;</span></p>
@snapend

@snap[north-east span-45  fragment]
<br>
<br>
<br>
<p style="line-height:40%"><span style="font-size:0.6em"><br><br><br>&nbsp;</span></p>
<p style="line-height:40%"><span style="font-size:0.6em"><br><br><br>&nbsp;</span></p>
<p style="line-height:40%"><span style="font-size:0.6em"><br><br><br>&nbsp;</span></p>
@box[bg-royal text-white rounded my-box-pad2 ](<p style="line-height:40%"><span style="font-size:0.6em">Ongoing tools to validate security mechanism<br> <br>&nbsp;</span></p>)
@snapend



Note:
- Tools and resources on how to test firmware for security
- Ongoing tools to validate security mechanism 


