

# How to run hello world application on a hardware design
#### In this tutorial we will be running a hello world application on a hardware design platform using the Xilinx Vitis IDE. Essentially, we are uploading this hello world application on the FPGA. Make sure you have satisfied all requirements under the Prerequisites section.

## Prerequisites
- Xilinx Vitis IDE - [install vivado & vitis](../install_vitis_and_vivado/install_vitis_and_vivado.md)
- A hardware .xsa file - [hello world tutorial](../hello_world_hw/hello_world_hw.m)
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
![image](platform_selected.jpg)

* Enter a name for the application then click *Next*
![image](app_name.jpg)

* The *Domain* page should be the same as the screen shot below then click *Next*
![image](domain.jpg)

* Select the *Hello World* as the development template then click *Finish*
![image](hw_template.jpg)


## Uploading the hello world program

* First let's build the project and assure there is no errors. Right click on the application then click *Build Project*
  *  Note - if you experience warnings, go to right click on application then click *Clean Project*
![image](app_right_click.jpg)

* By default the uart0 port is selected, we need to select uart1 as our serial port. Go to the platform file on the right middle window like below.
![image](tutorial_walkthru.jpg)

* Click on *Board Support Package* under *zynqmp_fsbl* which is under *psu_cortexa53_0*. Then click on *Modify BSP Settings...*
* Click on *standalone*. Change the *stdin* & *stdout* values to *psu_uart_1* then click *OK*
![image](uart1.jpg)

* Repeat the same step above for *Board Support Package* under *standalone on psu_cortexa53_0*

* Now let's open a serial monitor to see the printed contents of the *helloworld.c* file.

* Open the terminal and type **sudo minicom -s**. You will need to type in your password
![image](terminal.jpg

* Using your keyboard, scroll down to *Serial port setup* then press enter.
![image](serial_port.jpg)

* Change the *Serial Device* to **/dev/ttyUSB1** then press enter.
![image](usb1.jpg)

* Scroll down to *Save setup as defl* then scroll down to *Exit from Minicom*
![image](save_setup.jpg)

* Let's open up the serial port1 we just configured. On the terminal, type **sudo minicom** and enter your password. Keep the terminal running.
![image](port1_setup.jpg)

**Make sure the ultra96v2 FPGA board is connected to the power supply and the usb cable is connected from your computer to the USB-to-JTAG/UART pod**

* In Vitis IDE, right click on the application then *Debug As* -> *Launch Hardware*
  * This will upload the program on the FPGA board
![image](debug_as.jpg)

* The debugger will pop up now. Go ahead and click on the *step over* button until you step over the *print("Hello World\n\r");* line
![image](step_over.jpg) 

* Let's go back to the terminal. You should see the hello world text printed on the minicom in the serial port1 we configured above.
![image](hw_text.jpg)

