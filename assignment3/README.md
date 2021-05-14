# CMPE283 Assignment3

## work:
- Xueli Yang(Email:dafei19931207@gmail.com)
  Changing code in cpuid.c and vmx.c
Test on the code in inner vm

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

![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment3/hw3Screenshot/result1.jpg)
![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment3/hw3Screenshot/result2.jpg)

## Qeustions
  1. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail? 
  
  Made changes in the vmx_handle_exit function of the vmx.c file to calculate the number of exits by using the atomic_inc function. Atomic variables were used to make the system concurrent. The atomic variable was initialized in cpuid.c and exported in vmx.c using the export_symbol function.
  
  2. Of the exit types defined in the SDM, which are the most frequent? Least?
 
  Most Frequent Exit Types : 30 (IO Instruction), 28 (Control Register Accesses)
  Least Frequest Exit Types : 29 (MOV DR), 54 (WBINVD)
