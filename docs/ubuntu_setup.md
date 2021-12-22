# Creating and installing the Ubuntu Virtual Machine

## Creating a Ubuntu Virtual Machine

1. Start up Virtual Box and select *New*
![image](https://user-images.githubusercontent.com/96526387/147152239-87b05a6b-194b-4852-acbb-29dbbb3a7556.png)

2. VirtualBox will ask us to enter the name of the machine along with the type and version that we are going to use. 
In this case the type will be "Linux" and the version will be "Ubuntu (64-bit)". 
You can enter any name. This will be the one that allows you to identify your virtual machine in case you have more than one. 
In addition to this, it allows you to select the folder where the virtual machine files will be hosted. You can choose the folder you want, but you can also leave the one indicated by VirtualBox by default.
![image](https://user-images.githubusercontent.com/96526387/147152440-74e9f788-b9f3-490f-add1-15ff0acc8faa.png)

3. In the next step you will have to indicate the RAM memory your virtual machine will have. 
You want to ensure you have enough memory to install and run all the required packages, but not to allocate too much so that the rest of your machine becomes slow. 
As a minimum the size should be 2048 MB (2 GB) - for large projects give it at least 8000 MB (8GB). At first, you probably want to allocate somewhere in between 2 and 8 GB.
*Note*: if you run out of memory, or want to allocate more CPU power to your VM you can change these presets later (see below).

![image](https://user-images.githubusercontent.com/96526387/147152890-bd781cc9-2b31-4881-a6a8-d2d6a0052dee.png)

3. Next, Ubuntu will ask us to set up the hard drive. We will create a virtual disk. This step will create a file that will simulate the hard disk of your virtual machine. As you can see below, it will ask us what type of hard disk file we want to create. All the formats presented are valid for our purposes. 
VDI is the default format for VirtualBox, VDMK separates the disk into two 2GB files (this is neccesary for some file systems), and VHD is compatible with other virtualization systems. If you want to use your VM in other OS this may be the best option for you. 
To start, you can select VDI as the default. 
![image](https://user-images.githubusercontent.com/96526387/147153286-1c732555-6ed7-4dd0-958f-2e7a77583b66.png)
![image](https://user-images.githubusercontent.com/96526387/147153287-b15ac38e-51a6-4d75-8417-d8cc93bb9a2d.png)

4. Next, we are given two options to create the virtual hard disk. It asks us if we want the file to be dynamically allocated, that is if we want the space occupied by the VM to be equal to the size of the files, or if we want to give is a fixed size. 
The recommended option is to use the dynamically reserved disk so it does not take up unnecesary disk space. 
![image](https://user-images.githubusercontent.com/96526387/147153489-c2f8289a-86b6-4f9b-b74a-30aaa69924e6.png)

5. Then you will have to set the size for the disk. Ubuntu recommends using at least 25GB, but this will depend on the use you are going to give the VM and the files you are going to save inside the VM. 30GB is probably a good starting place. 
![image](https://user-images.githubusercontent.com/96526387/147153583-95c90415-fbf2-4dbd-8fc5-38a3648a1b89.png)

**We now have created our Ubuntu Virtual Machine.**
On the main screen you will be able to see the main chaacteristics you have defined for your virtual machine. 


Some items still need to be configured, these will be configured in the operating system installation process. The way to start this process will be by accessing the *Configuration* menu.

## Configuring your Ubuntu VM

1. In Settings go to "Storage"
![image](https://user-images.githubusercontent.com/96526387/147154098-88d9112d-c1ec-4a90-b26f-950561d98ea5.png)

Once in "Storage", we will select "Empty", just below "Controller:IDE". A section will appear on the right. Here we will click on the blue disk on the far right and click on «Select a disk file». Select the Ubuntu file that you have previously downloaded and click on "OK".

![image](https://user-images.githubusercontent.com/96526387/147153926-762d8fb7-afdc-43ef-9c14-0cee4f2854bb.png)
![image](https://user-images.githubusercontent.com/96526387/147154308-4e038c02-68b2-4ce1-9c0f-eaa9fc0bf3b2.png)

### Changing the characteristics of your Ubuntu VM
Once your Ubuntu VM is up and running you may find that you are running out of space. 
To change the space allocated for your VM go to *Settings* in the main VirtualBox menu. 
![image](https://user-images.githubusercontent.com/96526387/147154098-88d9112d-c1ec-4a90-b26f-950561d98ea5.png)

Under "System" you can change the Base Memory and Processing power allocated to your VM. 
![image](https://user-images.githubusercontent.com/96526387/147154649-44c481dd-3fa9-4dfc-ad46-939b76df8692.png)
![image](https://user-images.githubusercontent.com/96526387/147154670-2ff2cf09-bc8d-401f-8537-8e6ad0c08ada.png)
For reference - allocating 4 CPUs of processing power to your VM in this case means ~ half of your computer will be dedicated to running the VM when this is fired up. 

## Installing Ubuntu

The last step is to install the Ubuntu Operating System. To start with the installation you have to select *Show* or *Start*
![image](https://user-images.githubusercontent.com/96526387/147155006-26bf4eb6-0abd-40e2-b74e-b61226d5f7f5.png)

If VirtualBox doesn’t detect the Linux ISO, browse to its location by clicking the folder icon as shown in the picture below:
![image](https://user-images.githubusercontent.com/96526387/147155696-b8575c51-147a-428b-92ef-a122ad2aa983.png)

1. An operating system startup window will open. Usually at the beginning it does an error check on the disk, you have to let this process finish before proceeding. 
Before starting the installation, note that at some point you may see the mouse outside the VirtualBox window. This can happen because the program captures our mouse as if it belonged to the virtual machine that we are installing. 
To be able to use the mouse outside of our virtual machine you have to press the «Control» key on the right side of the keyboard.
![image](https://user-images.githubusercontent.com/96526387/147155220-5fb80c88-a451-4c3d-9518-89aa7301fdac.png)

Things from here are Ubuntu-specific. Other Linux distributions may have slightly different looking steps, but it won’t be complicated at all.

2. When the screen finishes we will get the following screen. It asks us if we want to test or directly install Ubuntu. 
Select *directly install*
![image](https://user-images.githubusercontent.com/96526387/147155779-4dd0ca96-ab1f-4abc-8080-cdb0848bbddc.png)

3. Next, it will ask us what type of installation we want to do. Select "Normal installation" with Ubuntu updates. 
Performing this step may cause the window to become small. If this is the case, without closing the installation window, go to "Settings" and change the resolution:

![image](https://user-images.githubusercontent.com/96526387/147156092-0ed5cc66-ab0e-465a-920d-46034e86e773.png)
![image](https://user-images.githubusercontent.com/96526387/147156131-6397b02d-ff30-4c1d-b10f-a070d75ba1b6.png)

Back to the install.

![image](https://user-images.githubusercontent.com/96526387/147156236-56417ffa-5ecd-4104-9578-75bd111b7b6e.png)

4. After this the installer will ask us where we want to install Ubuntu. Here we will select that we want to "Erase disk and install Ubuntu". Note that this wil not erase anything fro your personal computer, but rather, it will erase the virtual disk that we previously created with VirtualBox.
![image](https://user-images.githubusercontent.com/96526387/147156310-f454115a-687c-46b8-92d4-ae14fe9f3f28.png)
![image](https://user-images.githubusercontent.com/96526387/147156380-4b47a88a-42b2-4986-aeb0-06d30ada2876.png)

5. The installer will then ask you to indicate where you are to adjust your time zone. Select the time zone you most commonly work from, as this is hard to change later on. 

6. The next and last step before the installation starts is to set a machine name, username, and password. 
ill in the form and indicate whether or not we want to enter the password when starting a session. 
**You must put a password that you later remember AND is easy to type, since this will be needed to install programs and manage your operating system.**

![image](https://user-images.githubusercontent.com/96526387/147156714-f1609c4a-e81d-426f-b594-ccd33b808cd4.png)

Once this step is done, the install will start. Once the install finishes we will need to restart the VM. 
When restarting the virtual machine, before the machine shuts down, it will ask us to extract the installation media and press "Enter." As it is a virtual machine and we do not have installation means, simply press the "Enter" key.

Skip the linking accounts, and livepatch set up screens.

When the VM restarts it will likely show you a message that a newer Ubuntu version is available. Click remind me later, at this point you've gone through enough.









