# CMPE283 Assignment3

## work:
- Xueli Yang()

- Bo An (Email: bo.an.563641292@gmail.com)
  
  Work with Xueli to implete the features required by this assignment. And primarily worked on the cpuid.c and vmx.c to find out the nuber and frequency of exits of each type when cpuid leaf is called
  
## Procedures:
  1. worked on the kvm on Ubuntu20.04
  2. Follow the asssignment guildine to build the kernel to the latest version.
  3. research and watch the introduction of assignemnt video to get idea about what should we do in this assignment
  4. modify the vmx.c functions to calculate the number of exisit by using atomic varibale
  5. impletement the leaf function of 0x4ffffffe
  5. Test the modified kernel by using kvm
  
## Qeustions
  1. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail? 
  2. Of the exit types defined in the SDM, which are the most frequent? Least?
