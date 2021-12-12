**Home**
- [Home](../index.md)
---

# KVM Installation
**Follow link below:**  
(https://vitux.com/how-to-install-kvm-to-create-and-manage-virtual-machines-in-ubuntu/)
## Step 1: Verifying Hardware Support  
Before installing KVM, it is important to verify if your CPU supports virtualization and if the virtualization technology has been activated on your CPU.  
```bash
$ sudo apt-get install cpu-checker
$ egrep -c ‘(svm|vmx)’ /proc/cpuinfo
```  
The next thing to do is to check if the virtualization technology is enabled on your system or not as it is very important to run KVM. Use the following command in order to do so:
```bash
$ sudo kvm-ok
```
## Step 2: Installing the KVM Package
Now that you have verified the prerequisites for installing KVM on your system, use the following command to install KVM:
```bash
$ sudo apt-get install qemu-kvm libvirt-bin bridge-utils virt-manager
```

## Step 3: Adding Your User Account on KVM
The next step after the installation is to add your user account as a KVM user. It is important to note that you can use virtual machines on KVM only if you are a root user or if you are part of the libvirt/libvirtd group. Please use the following command to add yourself to the libvirtd group:
```bash
$ sudo adduser [username] libvirtd
```

Output 1:

The [username] has been added to the libvirtd group.

This is the output for slightly older versions of KVM that had a default group called libvirtd.

Output 2:

The same command might give the following output on your system:

Adding user to libvirtd group
This indicates that you are using a new version of KVM that has a default group libvirt serving the same purpose as that of the libvirtd group. The following output of the groups command will indicate that the current root user is already a member of the libvirt group. Therefore there is no need to add yourself to this group.

using groups command
For adding other users to this group use the following command:


The [username] has been added to the libvirtd group.

This is the output for slightly older versions of KVM that had a default group called libvirtd.

**Output 2:**

The same command might give the following output on your system:

Adding user to libvirtd group
This indicates that you are using a new version of KVM that has a default group libvirt serving the same purpose as that of the libvirtd group. The following output of the groups command will indicate that the current root user is already a member of the libvirt group. Therefore there is no need to add yourself to this group.

using groups command
For adding other users to this group use the following command:




