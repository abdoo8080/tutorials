# How to Install a Linux Virtual Machine 
#### In this tutorial we will be installing an Ubuntu 18.04.2 Linux virtual machine via the Oracle VirtualBox tool. This virtual machine will be used later to download the Vitis & Vivado environments. Although this tutorial is for mac users, Windows users can benefit from this as well. The tutorial is split into 3 sections: VirtualBox, Ubuntu installations, and how to configure VirtualBox to run the Ubuntu Linux OS.

### Prerequistes
* At least 8GB of RAM (recommended 16GB)
* At least 12GB of storage available for VirutalBox
* At least 160GB of storage available for the Vivado & Vitis environments


## Installing VirtualBox:
* Go to [VirtualBox Website](https://www.virtualbox.org/)
* Click on the big blue **Download VirtualBox x.x** where **x.x** is the version number
* Select **OS X hosts** (this is for a mac host)

![image](https://user-images.githubusercontent.com/49121005/109451227-97389580-7a12-11eb-90b2-05fa507061fc.png)


* Then go ahead and install it just like you would with any other application


### There's a chance you may get a security error when installing VirtualBox
  * To solve, go to **System Preferences** and under **General** in **Security & Privacy** you will see that VirtualBox is being blocked from making edits to your  mac. Allow it by checking the box, then proceed with installation.



## Now that we have VirtualBox, let's download the Unbuntu Linux operating system (OS)
* Go to the [Ubuntu Website](https://ubuntu.com/)
* In the navigation bar, click on **Developer** then **Develop on Ubuntu**

![image](https://user-images.githubusercontent.com/49121005/109452930-6b1f1380-7a16-11eb-882a-e174d46e9fb3.png)

* Then click on **Get Ubuntu now**

![image](https://user-images.githubusercontent.com/49121005/109453018-a4f01a00-7a16-11eb-9d14-8489adc99f31.png)

* Scroll down to the **Easy ways to switch to Ubuntu** section and click on **Software Updater**

![image](https://user-images.githubusercontent.com/49121005/109454351-a96a0200-7a19-11eb-9c6e-770c7d4fd75f.png)

* Under the **Before you start** section, click on **Ubuntu 18.04 LTS** link

![image](https://user-images.githubusercontent.com/49121005/109454575-24cbb380-7a1a-11eb-853b-4e18b9f32045.png)

* Scroll down to **Get Ubuntu 18.04.4 LTS** section and under **Download Ubuntu 18.04.4 LTS** click on the first link about ISOs and flashable images - http://releases.ubuntu.com/18.04.4/

![image](https://user-images.githubusercontent.com/49121005/109455027-47120100-7a1b-11eb-8e30-7436ffc86f97.png)

* Download the **ubuntu-18.04.2-desktop-amd64.iso** file which is 1.9GB (In orange)

![image](https://user-images.githubusercontent.com/49121005/109455410-2c8c5780-7a1c-11eb-915f-8d15d1d6e950.png)



## So far we have VirtualBox and the Ubuntu 18.04.2 Linux OS file installed. Let's configure VirtualBox so we can run Linux

* Open the VirtualBox application, which should open up like this:
![image](https://user-images.githubusercontent.com/49121005/109455782-f7343980-7a1c-11eb-9453-4233420c1bfa.png)

* Click on **New** and a small GUI titled **Name and operating system** will pop up
 * **Name** - give it a descriptive name. I named it after the version number
 * **Machine Folder** - this is where the Virtual Machine will be stored
 * **Type** - Linux
 * **Version** - Ubuntu (64-bit)
 
![image](https://user-images.githubusercontent.com/49121005/109456021-89d4d880-7a1d-11eb-9565-d2a9301eb87c.png)

* Click **Continue**. For **Memory size** I recommend you give it at least 8GB (8192MB)of your memory. Click **Continue**.
 * *Note* - if you need to free up some memory space later, you can re-adjust it at anytime in the VirtualBox settings

![image](https://user-images.githubusercontent.com/49121005/109456783-28156e00-7a1f-11eb-92ea-7b5d502b673e.png)

* For the **Hard disk** options, leave as is (**Create a virtual hard disk now**). Click **Create**.

![image](https://user-images.githubusercontent.com/49121005/109456902-6743bf00-7a1f-11eb-9cd6-ff95e91fcc65.png)

* **Hard disk file type** - select **VDI (VirtualBox Disk Image)**. Click **Continue**.

![image](https://user-images.githubusercontent.com/49121005/109457333-4b8ce880-7a20-11eb-9377-6adcb698e29c.png)

* For **Storage on physical hard disk**, select **Dynamically allocated**. Click **Continue**.
  * *Note*: this will dynamically take up what it needs, rather than a fixed space.
![image](https://user-images.githubusercontent.com/49121005/109457936-73c91700-7a21-11eb-9d76-cd7143a60a05.png)


* **File location and size** is for the hardware space (storage) allocated to the virtual machine. If you will be using Vivado/Vitis environments, give it at least 160GB of storage. The more, the better. *This allocation of storage **can not** be changed once set*. Click **Create** once done

![image](https://user-images.githubusercontent.com/49121005/109457827-3b293d80-7a21-11eb-9435-8250b0237454.png)

* And now we have our virtual machine. You should see something like this:
 
![image](https://user-images.githubusercontent.com/49121005/109458639-cbb44d80-7a22-11eb-844a-fe7bc4415d2e.png)

#### Let's configure the number of processors allocated to the virtual machine. 
* Go to **Settings** then **System** then **Processor**. The **Processor(s)** bar lets you select how many CPUs you want to give the virtual machine. I selected 4. Remember that Vivado/Vitis require a lot of processing especially when compiling things. The more you can give it the better. You may just have to play with it to find the right spot.

![image](https://user-images.githubusercontent.com/49121005/109458986-82183280-7a23-11eb-9d52-c0c4685d2573.png)

## Let's start this thing up.
* Click on **Start** (with the green arrow)
* You will be prompted to enter a file. This is the **.iso** file you downloaded earlier.

![image](https://user-images.githubusercontent.com/49121005/109459362-3e71f880-7a24-11eb-87e3-e409c2fa6247.png)

* Click on the yellow folder icon then click on **Add** and go locate wherever you put the **.iso** file and select it. Then click **Start**. 

![image](https://user-images.githubusercontent.com/49121005/109459562-a3c5e980-7a24-11eb-96e9-bd9666451aa7.png)

* Then Ubuntu will get powered up. It may take up some time to boot up.
* Once powered up, you will be prompted for some simple configurations such as Language, Time Zone, etc..

* Select **Install Ubuntu** when you get to the following configuration page:

![image](https://user-images.githubusercontent.com/49121005/109459863-38304c00-7a25-11eb-956e-ab26973a7b3d.png)

* Then for the following page, choose the selected options:
![image](https://user-images.githubusercontent.com/49121005/109460041-9eb56a00-7a25-11eb-98b0-4ac6f8926bd3.png)

* On the following page, choose **Erase disk and install Ubuntu**. Then click **Install Now**. Then click **Continue** for *writing the changes to disks**
![image](https://user-images.githubusercontent.com/49121005/109460159-c99fbe00-7a25-11eb-8f25-9e4bdbd27884.png)


* The rest is straight forward.

## That is it. We're done! We just installed Oracle VirtualBox and Ubuntu 18.04.2 to run a fully functiong Linux Virtual Machine.







