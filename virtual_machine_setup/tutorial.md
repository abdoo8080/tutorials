
# How to Install a Linux Virtual Machine 
#### In this tutorial we will be installing an Ubuntu 18.04.2 Linux virtual machine via the Oracle VirtualBox tool. This virtual machine will be used later to download the Vitis & Vivado environments. Although this tutorial is for mac users, Windows users can benefit from this as well. The tutorial is split into 3 sections: VirtualBox, Ubuntu installations, and how to configure VirtualBox to run the Ubuntu Linux OS.

### Prerequisites
* At least 8GB of RAM (recommended 16GB)
* At least 12GB of storage available for VirtualBox
* At least 160GB of storage available for the Vivado & Vitis environments


## Installing VirtualBox:
* Go to [VirtualBox Website](https://www.virtualbox.org/)
* Click on the big blue **Download VirtualBox x.x** where **x.x** is the version number
* Select **OS X hosts** (this is for a mac host)
![](virtalboxdownload.jpg)


* Then go ahead and install it just like you would with any other application


### There's a chance you may get a security error when installing VirtualBox
  * To solve, go to **System Preferences** and under **General** in **Security & Privacy** you will see that VirtualBox is being blocked from making edits to your  mac. Allow it by checking the box, then proceed with installation.



## Now that we have VirtualBox, let's download the Ubuntu Linux operating system (OS)
* Go to the [Ubuntu Website](https://ubuntu.com/)
* In the navigation bar, click on **Developer** then **Develop on Ubuntu**

![](ubuntu_1.jpg)

* Then click on **Get Ubuntu now**

![](ubuntu_desktop.jpg)

* Scroll down to the **Easy ways to switch to Ubuntu** section and click on **Software Updater**

![](3ways_to_switch.jpg)

* Under the **Before you start** section, click on **Ubuntu 18.04 LTS** link

![](before_you_start.jpg)

* Scroll down to **Get Ubuntu 18.04.4 LTS** section and under **Download Ubuntu 18.04.4 LTS** click on the first link about ISOs and flashable images - http://releases.ubuntu.com/18.04.4/

![](ubuntu_versions.jpg)

* Download the **ubuntu-18.04.2-desktop-amd64.iso** file which is 1.9GB (In orange)

![](ubuntu_desktopamd64.jpg)



## So far we have VirtualBox and the Ubuntu 18.04.2 Linux OS file installed. Let's configure VirtualBox so we can run Linux

* Open the VirtualBox application, which should open up like this:

![](peng.jpg)

* Click on **New** and a small GUI titled **Name and operating system** will pop up
 * **Name** - give it a descriptive name. I named it after the version number
 * **Machine Folder** - this is where the Virtual Machine will be stored
 * **Type** - Linux
 * **Version** - Ubuntu (64-bit)
 
![](name_and_OS.jpg)

* Click **Continue**. For **Memory size** I recommend you give it at least 8GB (8192MB)of your memory. Click **Continue**.
 * *Note* - if you need to free up some memory space later, you can re-adjust it at anytime in the VirtualBox settings

![](memory_size.jpg)

* For the **Hard disk** options, leave as is (**Create a virtual hard disk now**). Click **Create**.

![](hard_disk.jpg)

* **Hard disk file type** - select **VDI (VirtualBox Disk Image)**. Click **Continue**.

![](hard_disk_file_type.jpg)

* For **Storage on physical hard disk**, select **Dynamically allocated**. Click **Continue**.
  * *Note*: this will dynamically take up what it needs, rather than a fixed space.
![](storage_on_phydisk.jpg)


* **File location and size** is for the hardware space (storage) allocated to the virtual machine. If you will be using Vivado/Vitis environments, give it at least 160GB of storage. The more, the better. *This allocation of storage **can not** be changed once set*. Click **Create** once done

![](file_locn_and_size.jpg)

* And now we have our virtual machine. You should see something like this:
 
![](vm_with_ubuntu.jpg)

#### Let's configure the number of processors allocated to the virtual machine. 
* Go to **Settings** then **System** then **Processor**. The **Processor(s)** bar lets you select how many CPUs you want to give the virtual machine. I selected 4. Remember that Vivado/Vitis require a lot of processing especially when compiling things. The more you can give it the better. You may just have to play with it to find the right spot.

![](processor.jpg)

## Let's start this thing up.
* Click on **Start** (with the green arrow)
* You will be prompted to enter a file. This is the **.iso** file you downloaded earlier.

![image](empty.jpg)

* Click on the yellow folder icon then click on **Add** and go locate wherever you put the **.iso** file and select it. Then click **Start**. 

![image](ubuntu-20.04-desktop.jpg)

* Then Ubuntu will get powered up. It may take up some time to boot up.
* Once powered up, you will be prompted for some simple configurations such as Language, Time Zone, etc..

* Select **Install Ubuntu** when you get to the following configuration page:

![image](language_welcome.jpg)

* Then for the following page, choose the selected options:
![image](updates_and_other_swe.jpg)

* On the following page, choose **Erase disk and install Ubuntu**. Then click **Install Now**.

![image](installation_type.jpg)

* Then click **Continue** for *writing the changes to disks*.

![image](write_the_changes_to_disks.jpg)


* The rest is straight forward.

## That is it. We're done! We just installed Oracle VirtualBox and Ubuntu 18.04.2 to run a fully functioning Linux Virtual Machine.
