#CMPE283 Assignment 3
1. I've completed this lab myself.
2. a. I forked the linux repository on github. \
   b. I have a dual boot arch linux installation with windows, so I will be not be using vmware. \
   c. I cloned the forked repository to my local machine and made the necessary code changes. \
   d. I followed the instructions from https://wiki.archlinux.org/index.php/Kernel/Traditional_compilation to build and install the new kernel on my machine. \
   e. I started my machine with the new kernel and started a live Fedora 33 workstation in gnome boxes which uses kvm to run virtual machines. \
   d. In the live vm I installed cpuid ``sudo dnf install cpuid`` \
   f. Use cpuid to verify the new leaf function using ``cpuid --leaf=0x4FFFFFFE --subleaf=10`` or ``cpuid -1 --leaf=0x4FFFFFFE --subleaf=10`` \
   g. cpuid Output :
   ``CPU:
   0x4ffffffe 0x0a: eax=0x0000879a ebx=0x00000000 ecx=0x00000000 edx=0x00000000`` \
   h. We can also verify the new leaf function output in dmesg. \
   i. dmesg output : ``[ 1319.123696] kvm [2283]: leaf = 0x4FFFFFFE subleaf = 10, eax = 34714, ebx = 0, ecx = 0, edx = 0`` \
   j. I also added another leaf node to cpuid(0x4FFFFFFD) which prints counts of all exits in dmesg. \
   ``[  293.809922] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 0, count = 5875`` \
   ``[  293.809927] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 1, count = 114485`` \
   ``[  293.809930] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 2, count = 0`` \
   ``[  293.809932] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 3, count = 0`` \
   ``[  293.809934] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 4, count = 0`` \
   ``[  293.809936] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 5, count = 0`` \
   ``[  293.809938] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 6, count = 0`` \
   ``[  293.809940] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 7, count = 25074`` \
   ``[  293.809942] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 8, count = 0`` \
   ``[  293.809944] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 9, count = 0`` \
   ``[  293.809946] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 10, count = 33223`` \
   ``[  293.809948] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 11, count = 0`` \
   ``[  293.809950] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 12, count = 239769`` \
   ``[  293.809952] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 13, count = 0`` \
   ``[  293.809955] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 14, count = 0`` \
   ``[  293.809957] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 15, count = 0`` \
   ``[  293.809959] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 16, count = 0`` \
   ``[  293.809961] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 17, count = 0`` \
   ``[  293.809963] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 18, count = 5593`` \
   ``[  293.809965] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 19, count = 0`` \
   ``[  293.809967] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 20, count = 0`` \
   ``[  293.809969] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 21, count = 0`` \
   ``[  293.809971] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 22, count = 0`` \
   ``[  293.809973] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 23, count = 0`` \
   ``[  293.809975] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 24, count = 0`` \
   ``[  293.809977] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 25, count = 0`` \
   ``[  293.809979] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 26, count = 0`` \
   ``[  293.809981] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 27, count = 0`` \
   ``[  293.809983] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 28, count = 392884`` \
   ``[  293.809985] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 29, count = 12`` \
   ``[  293.809987] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 30, count = 88119`` \
   ``[  293.809989] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 31, count = 4048`` \
   ``[  293.809991] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 32, count = 127470`` \
   ``[  293.809994] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 33, count = 0`` \
   ``[  293.809996] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 34, count = 0`` \
   ``[  293.809997] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 35, count = 0`` \
   ``[  293.810000] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 36, count = 0`` \
   ``[  293.810002] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 37, count = 0`` \
   ``[  293.810004] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 38, count = 0`` \
   ``[  293.810006] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 39, count = 0`` \
   ``[  293.810008] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 40, count = 9938`` \
   ``[  293.810010] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 41, count = 0`` \
   ``[  293.810012] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 42, count = 0`` \
   ``[  293.810014] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 43, count = 0`` \
   ``[  293.810016] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 44, count = 11`` \
   ``[  293.810018] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 45, count = 0`` \
   ``[  293.810020] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 46, count = 56`` \
   ``[  293.810022] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 47, count = 22`` \
   ``[  293.810024] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 48, count = 291881`` \
   ``[  293.810026] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 49, count = 223906`` \
   ``[  293.810028] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 50, count = 0`` \
   ``[  293.810030] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 51, count = 0`` \
   ``[  293.810032] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 52, count = 111820`` \
   ``[  293.810034] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 53, count = 0`` \
   ``[  293.810036] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 54, count = 13`` \
   ``[  293.810038] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 55, count = 13`` \
   ``[  293.810040] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 56, count = 0`` \
   ``[  293.810042] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 57, count = 0`` \
   ``[  293.810044] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 58, count = 0`` \
   ``[  293.810046] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 59, count = 0`` \
   ``[  293.810048] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 60, count = 0`` \
   ``[  293.810050] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 61, count = 0`` \
   ``[  293.810052] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 62, count = 0`` \
   ``[  293.810054] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 63, count = 0`` \
   ``[  293.810056] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 64, count = 0`` \
   ``[  293.810058] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 65, count = 0`` \
   ``[  293.810060] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 66, count = 0`` \
   ``[  293.810062] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 67, count = 0`` \
   ``[  293.810064] kvm [2163]: leaf = 0x4FFFFFFD exit reason = 68, count = 0`` 

3. a. I observed the number of exits keeps increasing at a stable rate even with no applications running in the vm. \
   b. If we run applications in the vm then the rate of exits increases. \
   c. In my observation the full boot of a live fedora 33 workstation with gnome desktop and cpuid installation caused around ``1.6 million`` exits.
   
4. a. In the output above we see that many exit types are not occurring. Of the exits that are non-zero the most frequent is 28 Control-register accesses and among the least frequent exits are 29 MOV DR, 44 APIC access, 54 WBINVD, 55 XSETBV.
    
