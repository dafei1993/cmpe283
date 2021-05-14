# CMPE283 Assignment4

## work:
- Xueli Yang(Email:dafei19931207@gmail.com)
look on with ept

- Bo An (Email: bo.an.563641292@gmail.com. SID: 010695035)
  
 look on without ept

  
## Procedures:
  1. This assignment is based on the code of assignment 3 , so the first step is to run the assignment3 code
  2. after VM boot, run Dmesg to see the host machine and total count of exit type
  3. run command rmmod kvm-intel to remove the kvm intel module
  4. insert the vkm-intel module with ept = 0 to diable nested paging and enable shadow paging by command insmod /lib/modules/XXX/kernel/arch/x86/kvm/kvm-intel.ko ept=0
  5. reboot the VM and run Dmsg command to see the output message


## Qeustions



What did you learn from the count of exits? Was the count what you expected? If not, why not? 

What changed between the two runs (ept vs no-ept)?
When EPT is set to zero, we looked on the shadow paging approach instead of the nested paging approach followed when the EPT is not set to zero.  CR3 exits, Page Fault Exits and TLB Flush exits. These 3 types of exits occur in addition to the EPT. So that's why ept is more than no-ept
![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment4/hw4Screenshot/withept1.jpg)
noept 

![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment4/hw4Screenshot/noept.png)
