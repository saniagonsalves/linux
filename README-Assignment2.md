#CMPE283 Assignment 2
1. I've completed this lab myself.
2. a. I forked the linux repository on github. \
   b. I have a dual boot arch linux installation with windows, so I will be not be using vmware. \
   c. I cloned the forked repository to my local machine and made the necessary code changes. \
   d. I followed the instructions from https://wiki.archlinux.org/index.php/Kernel/Traditional_compilation to build and install the new kernel on my machine. \
   e. I started my machine with the new kernel and started a live Fedora 33 workstation in gnome boxes which uses kvm to run virtual machines. \
   d. In the live vm I installed cpuid ``sudo dnf install cpuid`` \
   f. Use cpuid to verify the new leaf function using ``cpuid --leaf=0x4FFFFFFF`` or ``cpuid -1 --leaf=0x4FFFFFFF`` \
   g. cpuid Output :
   ``CPU:
        0x4fffffff 0x00: eax=0x00196647 ebx=0x00000001 ecx=0x5baba59c edx=0x00000000`` \
   h. We can also verify the new leaf function output in dmesg. \
   i. dmesg output : ``[ 2970.784718] kvm [10583]: function = 0x4FFFFFFF, exits = 1664583, cycles = 5832943004, cycles_h = 1, cycles_l = 1537975708``
3. a. I observed the number of exits keeps increasing at a stable rate even with no applications running in the vm. \
   b. If we run applications in the vm then the rate of exits increases. \
   c. In my observation the full boot of a live fedora 33 workstation with gnome desktop and cpuid installation caused around ``1.6 million`` exits. 
    
