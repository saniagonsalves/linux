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
   j. I also added another leaf node to cpuid(0x4FFFFFFD) which prints counts of exits in dmesg. \
   ``[  265.072223] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 0, count = 5471 `` \
   ``[  265.072228] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 1, count = 129521 `` \
   ``[  265.072231] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 2, count = 0 `` \
   ``[  265.072233] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 3, count = 0 `` \
   ``[  265.072235] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 4, count = 0 `` \
   ``[  265.072237] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 5, count = 0 `` \
   ``[  265.072239] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 6, count = 0 `` \
   ``[  265.072241] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 7, count = 23323 `` \
   ``[  265.072243] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 8, count = 0 `` \
   ``[  265.072245] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 9, count = 0 `` \
   ``[  265.072247] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 10, count = 33455 `` \
   ``[  265.072249] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 11, count = 0 `` \
   ``[  265.072251] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 12, count = 229074 `` \
   ``[  265.072253] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 13, count = 0 `` \
   ``[  265.072255] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 14, count = 0 `` \
   ``[  265.072257] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 15, count = 0 `` \
   ``[  265.072259] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 16, count = 0 `` \
   ``[  265.072261] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 17, count = 0 `` \
   ``[  265.072263] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 18, count = 5572 `` \
   ``[  265.072265] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 19, count = 0 `` \
   ``[  265.072267] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 20, count = 0 `` \
   ``[  265.072269] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 21, count = 0 `` \
   ``[  265.072271] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 22, count = 0 `` \
   ``[  265.072274] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 23, count = 0 `` \
   ``[  265.072276] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 24, count = 0 `` \
   ``[  265.072278] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 25, count = 0 `` \
   ``[  265.072280] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 26, count = 0 `` \
   ``[  265.072282] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 27, count = 0 `` \
   ``[  265.072284] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 28, count = 1266470 `` \
   ``[  265.072286] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 29, count = 12 `` \
   ``[  265.072288] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 30, count = 82228 `` \
   ``[  265.072290] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 31, count = 4173 `` \
   ``[  265.072292] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 32, count = 124256 `` \
   ``[  265.072294] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 33, count = 0 `` \
   ``[  265.072296] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 34, count = 0 `` \
   ``[  265.072298] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 35, count = 0 `` \
   ``[  265.072300] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 36, count = 0 `` \
   ``[  265.072302] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 37, count = 0 `` \
   ``[  265.072304] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 38, count = 0 `` \
   ``[  265.072306] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 39, count = 0 `` \
   ``[  265.072308] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 40, count = 9830 `` \
   ``[  265.072310] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 41, count = 0 `` \
   ``[  265.072312] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 42, count = 0 `` \
   ``[  265.072314] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 43, count = 0 `` \
   ``[  265.072316] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 44, count = 11 `` \
   ``[  265.072318] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 45, count = 0 `` \
   ``[  265.072320] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 46, count = 56 `` \
   ``[  265.072322] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 47, count = 22 `` \
   ``[  265.072325] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 48, count = 291635 `` \
   ``[  265.072327] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 49, count = 217002 `` \
   ``[  265.072329] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 50, count = 0 `` \
   ``[  265.072331] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 51, count = 0 `` \
   ``[  265.072333] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 52, count = 111985 `` \
   ``[  265.072335] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 53, count = 0 `` \
   ``[  265.072337] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 54, count = 13 `` \
   ``[  265.072339] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 55, count = 13 `` \
   ``[  265.072341] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 56, count = 0 `` \
   ``[  265.072343] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 57, count = 0 `` \
   ``[  265.072345] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 58, count = 0 `` \
   ``[  265.072348] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 59, count = 0 `` \
   ``[  265.072350] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 60, count = 0 `` \
   ``[  265.072352] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 61, count = 0 `` \
   ``[  265.072354] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 62, count = 0 `` \
   ``[  265.072356] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 63, count = 0 `` \
   ``[  265.072358] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 64, count = 0 `` \
   ``[  265.072360] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 65, count = 0 `` \
   ``[  265.072362] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 66, count = 0 `` \
   ``[  265.072364] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 67, count = 0 `` \
   ``[  265.072366] kvm [2285]: leaf = 0x4FFFFFFD exit reason = 68, count = 0 `` 
   
3. a. I observed the number of exits keeps increasing at a stable rate even with no applications running in the vm. \
   b. If we run applications in the vm then the rate of exits increases. \
   c. In my observation the full boot of a live fedora 33 workstation with gnome desktop and cpuid installation caused around ``1.6 million`` exits.
   
4. a. In the output above we see that many exit types are not occurring. Of the exits that are non-zero the most frequent is 28 Control-register accesses and among the least frequent exits are 29 MOV DR, 44 APIC access, 54 WBINVD, 55 XSETBV.
    
