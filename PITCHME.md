---?image=assets/images/gitpitch-audience.jpg
@title[UEFI Platform Security]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI Platform Firmware Security

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Platform Security Pres

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
 <li>@fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Why is platform firmware Security important</span> </li>
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI boot flow with the threat model </span></li>
 <li>@fa[certificate gp-bullet-gold]<span style="font-size:0.9em">&nbsp;&nbsp;Security technologies overview</span> </li>
 <li>@fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;Tools and resources on how to test<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; firmware for security </span></li>
</ul>

---?include=Presentations/Why.md &image=assets/images/binary-strings-black2.jpg


Note:
-   ;?include=presentations/UEFI_Boot_Flow.md

-  ;?include=presentations/SecurityTechnologies.md

-   ;?include=presentations/Tools.md


---  
@title[Summary]
<BR>
### <p align="center"><span class="gold"   >Summary </span></p><br>
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Why is platform firmware Security important</span> </li>
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI boot flow with the threat model </span></li>
 <li>@fa[certificate gp-bullet-gold]<span style="font-size:0.9em">&nbsp;&nbsp;Security technologies overview</span> </li>
 <li>@fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;Tools and resources on how to test<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; firmware for security </span></li>
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

