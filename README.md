# cmpe-283-assignment-2 (0x4FFFFFFF and 0x4FFFFFFE)

## Q1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched.


- ## Mohaimin Iqbal Gazi(017454489)
  - Created virtual machine on Google Cloud engine
  - Installed new modules after building the kernel and then reloading the kernel
  - Researched the part of the codebase gone through by the Professor, to implement cpuid 0x4FFFFFFC and 0x4FFFFFFD.
  - Made code changes to vmx.c
  - Used rmmod to to install new modules after compiling the new code change
  - Modprobe to VM

- ## Hemang Huria(016123146)
  - Created VM inside a VM.
  - For some reasons, we were unable to create VM inside a VM in conventional way, so figured out a way to use Chrome Remote Desktop client after hours of research
  - Wrote test scripts to test the newly added cpuid functionality and verify things are working as expected
  - Took decision to use virt-manager after doing some research.
  - Improved the doc and suggested we cut the clutter by removing redundant screenshots because all the great open-source tool documentations rightfully do not provide screenshots when demonstrating step by step instructions.



## Q2. Describe in detail the steps you used to complete the assignment.

- Use the virtual instance we created in assignment 1 through the browser ssh window
- Apply the following commands (Most of the commands were taken from Professor Mike Larkin's lecture. We faced few issues which we solved by taking commands from google searching, stackoverflows, chatgpt etc...)
  - cd linux/arch/x86/kvm
  - Add the necessary code logics to the two files- "cpuid.c" and "vmx/vmx.c"
  - cd ~/linux
  - make -j 16 modules
  - sudo bash
    - make INSTALL_MOD_STRIP=1 modules install && make install
    - lsmod | grep kvm
    - rmmod kvm_intel
    - rmmod kvm
    - modprobe kvm
    - lsmod | grep kvm
    - modprobe kvm_intel
    - lsmod | grep kvm
- Create a VM inside the VM we are already working with
  - This behaviour can be achieved in multiple ways. We used "chrome remote desktop"
  - Use this wonderful tutorial on how to set up Chrome Remote Desktop for Linux on Google Compute Engine: https://cloud.google.com/architecture/chrome-desktop-remote-on-compute-engine
  - Go to the terminal inside the outer virtual machine and run
    - sudo apt-get update
    - sudo apt-get install virtual-manager
    - Launch a VM using the steps given here: https://cloud.google.com/architecture/chrome-desktop-remote-on-compute-engine
- Access the virtual manager using the chrome remote desktop client
- Write test scripts
- Run test script
