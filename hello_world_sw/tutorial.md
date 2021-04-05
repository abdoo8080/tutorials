

# How to run hello world application on a hardware design
#### In this tutorial we will be running a hello world application on a hardware design platform using the Xilinx Vitis IDE. Essentially, we are uploading this hello world application on the FPGA. Make sure you have satisfied all requirements under the Prerequisites section.

## Prerequisites
- Xilinx Vitis IDE - [install vivado & vitis](../install_vitis_and_vivado/install_vitis_and_vivado.md)
- An XSA file generated - [hello world tutorial](../hello_world_hw/hello_world_hw.m)
- Ultra96v2 board


## Creating the hardware design platform

* Open vitis and click on *Create Platform Project*
![image](vitis_firstpg.jpg)

* Enter a platform project name then click *Next*
![image](platform_prj_name.jpg)

* Click *Browse...* and go find the **.xsa** file you exported in [hello world tutorial](../hello_world_hw/hello_world_hw.m)
![image](xsa.jpg)

* Click *Finish*


## Creating the hello world application
#### Now that we have created the platform, let's create a new hello world application for it to run on top of it.

* Click *File* -> *Application Project...*
![image](new_app.jpg)

* Click *Next*
![image](2nd_app.jpg)

* Select the platfrom we have already created above then click *Next*
![image](platform_selected)

* Enter a name for the application then click *Next*
![image](app_name.jpg)

* The *Domain* page should be the same as the screen shot below then click *Next*
![image](domain.jpg)

* Select the *Hello World* as the development template then click *Finish*
![image](hw_template.jpg)


