# Hello World Hardware Design in Vivado
## Pre-requisites
- Setting up VM Enviornment
- Installing Vitis & Vivado on the VM Environment
- Installing the Ultra96v2 bdf Files

## Steps
1. Right click on your Ubuntu VM Desktop and open up a terminal.
2. Run the following commands to load the Vivado environment and IDE:
```bash
source /tools/Xilinx/Vivado/2020.1/settings64.sh
vivado
```
3. Once the Vivado IDE loads up, click on `Create Project` under `Quick Start` section.
![Create Project image](create_project.png "Click on Create Project")
4. A project wizard will show up to guide you through selecting design sources and a target device. Hit `Next`.
5. Name your project "hello_world_hw" and save it under your Desktop folder. Replace `<username>` with your user name. Hit `Next`.
![Set project name and location](name.png "Name your project hello_world_hw")
6. The next window specifies the project type. We're starting from scratch, so leave `RTL Project` selected and hit `Next`.
7. On the next window, we will select the Ultra96v2 development board as our target device. Switch to the `Boards` tab and select `Ultra96v2 Single Board Computer`. If you don't see the board, please go back to [Installing the Ultra96v2 bdf Files]() tutorial and ensure that they were installed correctly. Hit `Next`.
![Select Ultra96v2 board under Boards tab](board_selection.png "Seclect Ultra96v2 board").
8. The next window shows a summary of our project. It should look like the window below. Hit `Finish`.
![Project summary](summary.png "Project summary").