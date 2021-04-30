# Assignment2

---
### 1. Xueli Yang : (dafei19931207@yahoo.com, Student Id:008737742)

1. Install ubuntu 20.0.04 version desktop
2. Build Linux Kernel on my machine
3. Install KVM 
4. write code for cpuid.c
---
### 2. Bo An : (Email: bo.an.563641292@gmail.com, Student Id: 010695035)

1. Build Linux kernel 
2. Install KVM inside ubuntu
3. search what is atomic variable and how to use them.
4. write vmx.c

---
### Procedures


1. Install ubuntu for prepartion,clone linux kernel from fork repository：git clone https://github.com/torvalds/linux.git
2. Install all libs that needed for building linux kernel by command ***sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf***
3. Check current kernel version by ***uname -a***
4. Copy config file by command ***cp /boot/config-5.8.0-50-generic ./.config***
5. Make default configuration ***make oldconfig*** 
6. Find a line called CONFIG_SYSTEM_TRUSTED_KEYS = "debian/canonical-certs.pem" change it to CONFIG_SYSTEM_TRUSTED_KEYS="". Otherwise, there will be an error while building kernel
7. Building kernel with command ***make -j 4 modules && make -j 4 && sudo make modules_install && sudo make install*** 
8. Install kvm
9. Install requied tools ***sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager***
10. Add user ***sudo adduser user1 libvirt && sudo adduser user1 libvirt-qemu***
11. Creating a Vm with virt manager
12. Modify the vmx.c and cpuid.c 
13. Rebuild and reboot the modified kernel
14. Emulate cpuid instruction with CPUID packed installed in KVM(sudo apt-get install cpuid)
15. Get result
![output1](https://github.com/dafei1993/cmpe283/blob/main/assignment2/screenshot/58ca13e59ba9a420b85937ac55269cb.png)
