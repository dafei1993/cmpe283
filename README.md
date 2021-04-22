# CMPE281 homework assignment 1

  ## Work Distribution
---
### 1. Xueli Yang : (dafei19931207@yahoo.com, Student Id:008737742)

1. Download and configure VMware Fushion.app with Ubuntu server on my desktop 
2. Read the VMX configuration MSRs on SDM 
3. write code for scondary procbased controls/entry

---
### 2. Bo An : (Email: bo.an.563641292@gmail.com, Student Id: 010695035)

1. Download and configure VMware worksation on my desktop 
2. Read the VMX configuration MSRs on SDM to get idea about what capabilities/Features should be enabled for different controls
3. write code for Exit/ProcessBased controls

---

## Work Procedures

1. Download VMware fusion/workstation from the VMware website(VM fusion is for mac OS and workstation is for windows OS)

2. Install the application of your choice

3. After installation, from the VMware home panel, create a Virtual machine.

4. In order to have a good experience with later Homework Assignment, the disk storage of the VM should be larger than 100G(as Professor said after building the linux kernel the size of it might grow to a large amount and it is better to give enough space in the beginning)
 
5. Also, VT-X/EPT need to be enabled under the setting panel of VM(it may also have a different name called enable hardware virtualization assist...)

6. On github, clone the linux repository to own github repository(https://github.com/torvalds/linux)
 
7. Open the newly created VM, install git on linux(this step is required to clone linux repository to your machine, and the command is ***sudo install git on linux***)

8. clone the linux repository from github to local by using command ***git clone “your git url”*** (this url should without quote mark)(this step takes me about 10-15mins because my network is slow and the size of it is 3.97GB)

9. Download the makefile and cmpe283-1.c to on VM from mysjsu 

10. Install required packages to build a kernel(https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) (The first command does not work on my VM so I used the second one)
Command : ***sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf***

11. Research the controls need to be used in this assignment.
    | MSR Name  | MSR Index  | Notes | SDM location |
    | ----------- | ----------- | ----------- | ----------- |
    | IA32_VMX_PINBASED_CTLS  | 0x481  | Use this MSR for pinbased controls if no true controls capability  | SDM volume 3, section 24.6.1 |
    | IA32_VMX_PROCBASED_CTLS  | 0x482  | Use this MSR for procbased controls if no true controls capability  | SDM volume 3C, section 24.6.2 |
    | IA32_VMX_PROCBASED_CTLS2  | 0x48B  | Use this MSR for secondary procbased controls, if available  | SDM volume 3, section 24.6.2 |
    | IA32_VMX_EXIT_CTLS  | 0x483  | Use this MSR for exit controls if no true controls capability  | SDM volume 3C, section 24.7.1 |
    | IA32_VMX_ENTRY_CTLS  | 0x484  | Use this MSR for entry controls if no true controls capability  | SDM volume 3C, section 24.8.1 |
12. Implement code in cmpe283-1.c
  - define the different controls
  ``` C language
    #define IA32_VMX_PINBASED_CTLS 0x481
    #define IA32_VMX_ENTRY_CTLS 0x484
    #define IA32_VMX_EXIT_CTLS 0x483
    #define IA32_VMX_PROCBASED_CTLS 0x482
    #define IA32_VMX_PROCBASED_CTLS2 0x48B
  ```
  - define pinbased capabilities
   ``` C language
    struct capability_info pinbased[5] =
    {
      { 0, "External Interrupt Exiting" },
      { 3, "NMI Exiting" },
      { 5, "Virtual NMIs" },
      { 6, "Activate VMX Preemption Timer" },
      { 7, "Process Posted Interrupts" }
    };
  ```
  - define procbased capabilities
  ```C
  struct capability_info procbased[21] =
    {
      { 2, " Interrupt-window exiting" },
      { 3, "Use TSC offsetting " },
      { 7, "HLT exiting " },
      { 9, "INVLPG exiting " },
      { 10, "MWAIT exiting" },
      { 11, "RDPMC exiting" },
      { 12, "RDTSC exiting" },
      { 15, "CR3-load exiting" },
      { 16, "CR3-store exiting" },
      { 19, "CR8-load exiting" },
      { 20, "CR8-store exiting" },
      { 21, "Use TPR shadow " },
      { 22, "NMI-window exiting" },
      { 23, "MOV-DR exiting" },
      { 24, "Unconditional I/O exiting" },
      { 25, "Use I/O bitmaps " },
      { 27, "Monitor trap flag " },
      { 28, "Use MSR bitmaps" },
      { 29, "MONITOR exiting" },
      { 30, "PAUSE exiting" },
      { 31, "Activate secondary controls" }
    }; 
```
  - define secondary procbased capabilities
```
  struct capability_info secondary_procbased[23] =
  {
    { 0, " Virtualize APIC accesses" },
    { 1, "Enable EPT " },
    { 2, "Descriptor-table exiting " },
    { 3, "Enable RDTSCP " },
    { 4, "Virtualize x2APIC mode" },
    { 5, "Enable VPID" },
    { 6, "WBINVD exiting" },
    { 7, "Unrestricted guest" },
    { 8, "APIC-register virtualization" },
    { 9, "Virtual-interrupt delivery" },
    { 10, "PAUSE-loop exiting" },
    { 11, "RDRAND exiting " },
    { 12, "Enable INVPCID" },
    { 13, "Enable VM functions" },
    { 14, "VMCS shadowing" },
    { 15, "Enable ENCLS exiting " },
    { 16, "RDSEED exiting " },
    { 17, "Enable PML" },
    { 18, "EPT-violation #VE" },
    { 19, "Conceal VMX non-root operation from Intel PT" },
    { 20, "Enable XSAVES/XRSTORS" },
    { 22, "Mode-based execution control for EPT" },
    { 25, "Use TSC scaling" }
  }; 
```
 - define entry controls capabilities
```C
    struct capability_info entry_controls[9] =
    {
      { 2, "Load debug controls" },
      { 9, "IA-32e mode guest" },
      { 10, "Entry to SMM" },
      { 11, "Deactivate dual-monitor treatment " },
      { 13, "Load IA32_PERF_GLOBAL_CTRL" },
      { 14, "Load IA32_PAT" },
      { 15, "Load IA32_EFER" },
      { 16, "Load IA32_BNDCFGS" },
      { 17, "Conceal VM entries from intel PT" }
    };
```
- define exit controls capabilities

```c
    struct capability_info exit_controls[11] =
    {
      { 2, "Save debug controls" },
      { 9, "Host address-space size" },
      { 12, "Load IA32_PERF_GLOB AL_CTRL" },
      { 15, "Acknowledge interrupt on exit " },
      { 18, "Save IA32_PAT" },
      { 19, "Load IA32_PAT" },
      { 20, "Save IA32_EFER" },
      { 21, "Load IA32_EFER" },
      { 22, "Save VMX-preemption timer value" },
      { 23, "Clear IA32_BNDCFGS" },
      { 24, "Conceal VM exits from Intel PT" }
    };

```
13. save the file, and use command ***make*** to compile the cmpe283-1.c, this command will generate lots of files including a file called "cmpe283-1.ko" this is a file that can be loaded in to kernel

14. then use command ***sudo insmod ./cmpe283-1.ko*** load the file
15. use command ***dmesg*** show the result message
16. after this process, if you want to remove the module from kernel, your can use this command ***sudo rmmod ./cmpe283-1.ko***
17. and ***make clean*** is used to clean all files generated by the ***make*** command
![output1](https://github.com/dafei1993/cmpe283/blob/main/hw1ScreenShot/output1.png)
![output1](https://github.com/dafei1993/cmpe283/blob/main/hw1ScreenShot/output2.png)
![output1](https://github.com/dafei1993/cmpe283/blob/main/hw1ScreenShot/output3.png)
