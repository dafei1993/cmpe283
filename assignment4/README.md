# CMPE283 Assignment4

## work:
- Xueli Yang(Email:dafei19931207@gmail.com)
Changing code in cpuid.c and vmx.c
Test on the code

- Bo An (Email: bo.an.563641292@gmail.com. SID: 010695035)
  
  reaseach and write code for executing the primary and secondary VM based control. And implment their outputs in hte test fiel and README.md file

  
## Procedures:
  1. This assignment is based on the code of assignment 3 , so the first step is to run the assignment3 code
  2. after VM boot, run Dmesg to see the host machine and total count of exit type
  3. run command rmmod kvm-intel to remove the kvm intel module
  4. insert the vkm-intel module with ept = 0 to diable nested paging and enable shadow paging by command insmod /lib/modules/XXX/kernel/arch/x86/kvm/kvm-intel.ko ept=0
  5. reboot the VM and run Dmsg command to see the output message


## Result:


## Qeustions
1.For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).

2.Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”. 

3.What did you learn from the count of exits? Was the count what you expected? If not, why not? 

4.What changed between the two runs (ept vs no-ept)?
