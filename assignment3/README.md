# CMPE283 Assignment3

## work:
- Xueli Yang(Email:dafei19931207@gmail.com)

  Changing code in cpuid.c and vmx.c and did the testing on the code in inner vm

- Bo An (Email: bo.an.563641292@gmail.com)
  
  Work with Xueli to implete the features required by this assignment. And primarily worked on the cpuid.c and vmx.c to find out the nuber and frequency of exits of each type when cpuid leaf is called
  
## Procedures:
  1. worked on the kvm on Ubuntu20.04
  2. Follow the asssignment guildine to build the kernel to the latest version.
  3. research and watch the introduction of assignemnt video to get idea about what should we do in this assignment
  4. modify the vmx.c functions, made changes in the vmx_handle_exit function to calculate the number of exisit by using atomic varibale
  5. impletement the leaf function of 0x4ffffffe
  6. Test the modified kernel by using kvm

## Result:

![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment3/hw3Screenshot/result2.jpg)

## Qeustions
  1. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail? 
  
  The number of exits increase at a stable rate. There are around 5.6 million exits when a full VMboot entail.
  
  2. Of the exit types defined in the SDM, which are the most frequent? Least?
 
  Most Frequent Exit Types : 30 (IO Instruction), 28 (Control Register Accesses)
  Least Frequest Exit Types : 29 (MOV DR), 54 (WBINVD)
