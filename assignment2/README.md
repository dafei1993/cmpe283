# Assignment2

---
### 1. Xueli Yang : (dafei19931207@yahoo.com, Student Id:008737742)

1. Download and configure VMware Fushion.app with Ubuntu server on my desktop 
2. Read the VMX configuration MSRs on SDM 
3. write code for scondary procbased controls/entry

---
### 2. Bo An : (Email: bo.an.563641292@gmail.com, Student Id: 010695035)

1. Build Linux kernel 
2. Install KVM inside ubuntu
3. search what is atomic variable and how to use them.
4. write vmx.c

---
### Procedures

1. clone linux kernel from fork repository
2. install all libs that needed for building linux kernel by command ***sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf***
3. check current kernel version by ***uname -a***
4. copy config file by command ***cp /boot/config-5.8.0-50-generic ./.config***
5. make default configuration ***make oldconfig*** 
6. find a line called CONFIG_SYSTEM_TRUSTED_KEYS = "debian/canonical-certs.pem" change it to CONFIG_SYSTEM_TRUSTED_KEYS="". Otherwise, there will be an error while building kernel
7. building kernel with command ***make -j 4 modules && make -j 4 && sudo make modules_install && sudo make install*** 
8. install kvm
9. install requied tools ***sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager***
10. add user ***sudo adduser user1 libvirt && sudo adduser user1 libvirt-qemu***
11. Creating a Vm with virt manager
12. modify the vmx.c and cpuid.c 
13. rebuild and reboot the modified kernel
14. emulate cpuid instruction with CPUID packed installed in KVM(sudo apt-get install cpuid)
15. get result
![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment2/screenshot/output.PNG)
