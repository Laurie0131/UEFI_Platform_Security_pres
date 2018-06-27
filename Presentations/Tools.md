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
<p align="right"><span class="gold" ><b>Build a Security Mindset</b></span></p>
<div class="left">
<br>
<span style="font-size:0.7em" >“Finding BIOS Vulnerabilities with Symbolic Execution and Virtual Platforms”: <a href="https://software.intel.com/en-us/blogs/2017/06/06/finding-bios-vulnerabilities-with-excite"> Excite Link</a></span>
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
<p align="right"><span class="gold" ><b>What is Excite?</b></span></p>
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
<ul style="list-style-type:none">
  <li><span style="font-size:0.5em" >AFL - American Fuzzy Lop (fuzzer)</span></li>
  <li><span style="font-size:0.5em" >Pin – Intel tool to determine trace</span></li>
  <li><span style="font-size:0.5em" >CRETE -<a href="https://github.com/SVL-PSU/crete-dev"> github crete-dev</a> </span></li>
</ul>

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
<p align="right"><span class="gold" ><b>What is Fuzzing?</b></span></p>
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
<p align="right"><span class="gold" ><b>Symbolic Execution  (S2E)– SMM Example</b></span></p>
<br>
<div class="left1">
<ul style="list-style-type:disc">
  <li><span style="font-size:0.8em" >Searching for SMM security vulnerabilities </span> </li>
  <li><span style="font-size:0.8em" >Symbolic execution generates test cases that cover the computation tree of the handler and induce vulnerabilities. </span> </li>
  <li><span style="font-size:0.8em" >Those test cases are replayed in Simics which detects illegal accesses and SMM callouts. (e.g. read memory outside SMRAM) </span> </li>
</ul>
<br>
<span style="font-size:0.5em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Symbolic execution for BIOS security<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <a href="https://www.usenix.org/system/files/conference/woot15/woot15-paper-bazhaniuk.pdf">woot15-paper-bazhaniuk PDF </a> </span>
</div>
<div class="right1">
<span style="font-size:0.8em" > &nbsp;</span> 
</div>

Note: 
 
- Given a snapshot of SMRAM, the base address of SMRAM, and the address of the variable interrupt handler in SMRAM, the tool uses S2E to run the symbolic execution engine to search for concrete examples of a call to the SMI interrupt handler that causes the handler to read memory outside of SMRAM
  
 
---?image=/assets/images/slides/Slide152.JPG
@title[Excite - Common Flow]
<p align="right"><span class="gold" ><b>Excite - Common Flow</b></span></p>

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
<p align="right"><span class="gold" ><b>Excite Benefits</b></span></p>
<br>
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><b>Extend fuzzing beyond interface level </b></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.8em" >UEFI code (SMM, STM, UEFI PE modules) accessible to AFL/CRETE, Pin, gdb. </span>  </li>
    <li><span style="font-size:0.8em" >Record/analyze code flow, call trace, memory access data  </span>  </li>
    <li><span style="font-size:0.8em" >Individual functions accessible, new inputs created, can test different flows</span>  </li>
  </ul>
  <li><span style="font-size:0.8em" ><b>Quantify code coverage reporting </b></span>  </li>
</ul>
<br>
<br>
<span style="font-size:0.5em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Resource: <a href="https://firmware.intel.com/content/smi-transfer-monitor-stm ">STM-SMI Transfer Monitor </a></span>

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
  

 
---?image=/assets/images/slides/Slide156.JPG
@title[Raising the Bar for Platform Security]
<p align="center"><span class="gold" ><b>Raising the Bar for Platform Security</b></span></p>
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
<span style="font-size:0.5em" >Source: <a href="https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf">CHIPSEC-csw14 PDF </a></span>

Note:
- Source: https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf

- What if there was a tool to help us determine if the Platform Code is doing the right thing?

- As New attacks are discovered 
  - Research is done determining the root cause  of the attack

- Then a test could be done to test that a platform does not expose that vulnerability

- Introducing CHIPSEC

 
---?image=/assets/images/slides/Slide158.JPG
@title[What is CHIPSEC?]
<p align="center"><span class="gold" ><b>What is CHIPSEC?</b></span></p>
<br>
<div class="left2">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><font color="yellow"><b>Framework for Platform Security Assessment</b></font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Tests for known security issues</span>  </li>
    <li><span style="font-size:0.7em" >Tools for investigation of platform properties</span>  </li>
  </ul>
  <li><span style="font-size:0.8em" ><font color="yellow"><b>Open Source (GPLv2 License)</b></font></span>  </li>
  <ul style="list-style-type:disc">
    <li><span style="font-size:0.7em" >Released in 2014 – @fa[github gp-bullet-white]<span style="font-size:0.7em"><a href="https://github.com/chipsec/chipsec "> https://github.com/chipsec/chipsec </a></span></span>  </li>
    <li><span style="font-size:0.7em" >Currently active community</span>  </li><br>
    <li><span style="font-size:0.7em" >Top referring sites: </span><span style="font-size:0.6em" >Google, Github, <a href="">pcworld.com</a>, 
	<a href="">community.spiceworks.com</a>,
	<a href="">anonhq.com</a>, Twitter, <a href="">securingtomorrow.mcafee.com</a>,
	<a href="">intelsecurity.com</a>,
	<a href="">cylance.com</a></span>  </li>
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

 
---?image=/assets/images/slides/Slide160.JPG
@title[Chipsec Framework overview]
<p align="center"><span class="gold" ><b>Chipsec Framework overview</b></span></p>

Note:

 
---?image=/assets/images/slides/Slide158_1.JPG
@title[Example Chipsec Check - SPI Controller LOCK]
<br>
<p align="center"><span class="gold" ><b>Example Chipsec Check - SPI Controller LOCK</b></span></p>
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


---?image=/assets/images/slides/Slide158_1.JPG
@title[Sample Issue Discovered]
<br>
<p align="center"><span class="gold" ><b>Sample Issue Discovered</b></span></p>
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



---
@title[Known Threats and Chipsec modules]
<p align="center"><span class="gold" ><b>Known Threats and Chipsec modules</b></span></p>
<table border="1" width="100%">
	<tr>
		<td bgcolor="#0071c5">Issue</td>
		<td bgcolor="#0071c5">CHIPSEC Module</td>
		<td bgcolor="#0071c5">References</td>
	</tr>
	<tr>
		<td>1 tbd&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>2&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>3&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>4&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>5&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>6&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
</table>

Note:
Source: https://cansecwest.com/slides/2014/Platform%20Firmware%20Security%20Assessment%20wCHIPSEC-csw14-final.pdf



---?image=/assets/images/slides/Slide158_1.JPG
@title[CHIPSEC Modules ]
<br>
<p align="center"><span class="gold" ><b>CHIPSEC Modules </b></span></p>
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


---?image=/assets/images/slides/Slide158_1.JPG
@title[CHIPSEC Modules ]
<br>
<p align="center"><span class="gold" ><b>CHIPSEC Modules </b></span></p>
<span style="font-size:0.9em" >Modules encapsulate the main functionality of CHIPSEC:</span> 
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

---?image=/assets/images/slides/Slide176.JPG
@title[Summary 4 - Platform Firmware Security – Why is it important? ]
<p align="right"><span class="gold" ><b>Summary <br>Platform Firmware Security – Why is it important?</b></span></p>
<br>
<br>
<br>
<br>

Note:
