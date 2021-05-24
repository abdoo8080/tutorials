# Install Petalinux OS
## Description
This tutorial lists the steps to install the Petalinux OS and save it in an SD card image to boot in the Ultra96v2 development board.

## Pre-requisites
- [Install Vitis and Vivado IDEs](../install_vitis_and_vivado/README.md)

## Steps
1. Start by downloading the AVNET's repositories to install the Vitis platform:
    ```bash
    cd ~/project/2020.2
    git clone https://github.com/Avnet/bdf
    git clone -b 2020.2 https://github.com/Avnet/hdl
    git clone -b 2020.2 https://github.com/Avnet/petalinux
    git clone -b 2020.2 https://github.com/Avnet/vitis
    ```
2. Move into the the vitis directory and build AVNET's base the hardware design.
    ```bash
    cd vitis
    source /tools/Xilinx/Vitis/2020.2/settings64.sh
    source /tools/Xilinx/PetaLinux/2020.2/tool/settings.sh
    make u96v2_sbc step=xsa
    ```
3. Optional: to enable profiling of applications running on the board, you will need to modify AVNET's Petalinux configurations. Open `make_u96v2_sbc_base.sh` in an editor:
    ```bash
    gedit ../petalinux/scripts/make_u96v2_sbc_base.sh
    ```
    Add the following 2 lines after line 83 of the script:
    ```bash
    petalinux-config -c kernel
    petalinux-config -c rootfs
    ```
    Save your changes and close the editor.
4. To install Petalinux OS, run the following command:
    ```bash
    make u96v2_sbc step=plnx
    ```
    If you went through step 3, a new terminal window will pop up allowing you to configure the kernel. Enable the following settings:
    ```
    General architecture-dependent options ---> [*] Kprobes
    Kernel hacking ---> [*] Tracers
    Kernel hacking ---> [*] Tracers --->

    [*] Kernel Function Tracer

    [*] Enable kprobes-based dynamic events

    [*] Enable uprobes-based dynamic events
    ```
    Save your changes and exit. Another terminal window will pop up allowing you to configure the root file system. Enable the following setting:
    ```
    user-packages ---> modules ---> [*] packagegroup-petalinux-self-hosted
    ```
    Save your changes and exit.



make u96v2_sbc step=sysroot
make u96v2_sbc step=pfm
