# its452
course materials and references for its452

## lab01: Build environments for computer forensics
* Create virtual machines
* Setup Forensics Tools
* *Rule of thumb to choose software: always choose the latest and STABLE version*

**You don't need a Windows server if your computer OS is Windows, you may install the forensics tools on the host OS**

## NAT network and VM settings
* NAT network settings:
  * Disable IPv6
  * Network ID: 10.20.30.0
* VM settings: one for Ubuntu, one for Windows server
  * *6GB memory/200GB disk*
  * Connect to the NAT network
  * It is a best practice to set VM's IP address statically
  * Enable network promiscuous mode

## Install Ubuntu  Mate LTS
Follow the steps below to setup Ubuntu  Mate in a VirtualBox VM:

1. Download [Ubuntu MATE LTS](https://ubuntu-mate.org/) from its official website --- [https://ubuntu-mate.org](https://ubuntu-mate.org). Choose the  64-bit PC version ubuntu-mate LTS.
2. (20%)Create a VM with *6GB memory/200GB disk* in VirtualBox and install the downloaded Ubuntu


After installation, *make sure you can access Internet*, update and upgrade Ubuntu, then install the following tools. Open a terminal window, run the following commands:

```bash
sudo apt update
sudo apt upgrade
sudo apt install p7zip-full build-essential gcc perl cmake automake curl git
```

### (20%)Install Java Environment
In this class, both Java JDK 8 & 11 are needed, a tool named [sdkman](https://sdkman.io/) can manage multiple-version Java JDK. Run the following commands to install *sdkman* first:

```bash
curl -s "https://get.sdkman.io" | bash
source .sdkman/bin/sdkman-init.sh 
sdk version
sdk list java
ln -s .sdkman sdkman
```


Now it is ready to install Java JDK 8 \& 11, run the following commands:

```bash
sdk list java
# choose the suitable versions from the list
sdk install java 8.0.265.fx-librca
sdk install java 11.0.8.fx-librca
```

### (20%)Install Sleuth Kit & Autopsy

We will use the latest-version *Sleuth Kit  & Autopsy*. They are *state-of-the-art* forensics tools. 

Follow the steps below to setup Sleuth Kit & Autopsy:

1. Download [sleuthkit-java, Autopsy & sleuthkit source code](https://www.sleuthkit.org) from its official website [https://www.sleuthkit.org](https://www.sleuthkit.org)

By default, the downloaded files are saved at the Download folder in your home directory. Go to the folder where all the above downloaded files reside, open a terminal and run the following commands:

```bash
sdk default java 8.0.265.fx-librca
sudo apt install testdisk

# replace x.x.x-x with the corresponding version numbers
sudo apt install ./sleuthkit-java_x.x.x-x_amd64.deb
# replace y.y.y with the corresponding version numbers
7z x autopsy-y.y.y.zip
cd autopsy-y.y.y
JAVA_HOME="/home/$USER/.sdkman/candidates/java/current"
export JAVA_HOME
chmod +x unix_setup.sh
./unix_setup.sh

# 2021 Fall, first time run autopsy
./bin/autopsy --nosplash

# later run autopsy
./bin/autopsy
```

The last line  above runs Autopsy. If everything goes well, Autopsy should show up, close Autopsy.
Go back to the terminal window above, run the following commands to compile and install Sleuth Kit:

```bash
cd ..
# replace x.x.x with the corresponding version numbers
tar zxf sleuthkit-x.x.x.tar.gz
cd sleuthkit-x.x.x/
./configure
make
sudo make install
```

### (20%)Install [Bulk extractor](http://downloads.digitalcorpora.org/downloads/bulk_extractor/)
Run the following commands to install [bulk extractor](https://github.com/simsong/bulk_extractor):

If the official repository does not work, please use this [link](https://drive.google.com/file/d/17DcYmxEIcvzG87kafg1IGIwnROzXCVt2/view?usp=sharing) to download a worked copy.

```bash
sdk default java 11.0.8.fx-librca
sudo apt install libssl-dev libxml2-dev flex
git clone https://github.com/simsong/bulk_extractor.git
cd bulk_extractor/

chmod +x bootstrap.sh 
./bootstrap.sh 
./configure 
make
sudo make install

bulk_extractor 
BEViewer
```

### Set the correct Java JDK before running programs
Set the correct Java JDK before you run programs. For example:

```bash
# 1. Run autopsy
sdk default java 8.0.265.fx-librca

# go to the folder where your autopsy resides
./bin/autopsy

# 2. Run BEViewer
sdk default java 11.0.8.fx-librca

BEViewer
```

## Install Windows server

*If your host operating system is Windows, then you don't need to install Windows server.*

* Download [Windows Server](https://www.microsoft.com/en-us/windows-server)
* Create a Virtual Machine with *6GB memory/200GB disk* in VirtualBox for installing this Windows server
* Install the Windows Server for a free trial
* (10%) Install Sleuth Kit & Autopsy
* (10%) Install [Bulk extractor](https://github.com/simsong/bulk\_extractor). BEViewer also provides a User Interface for launching bulk_extractor scans, it is packaged with bulk_extractor. BEViewer needs to be built under Linux, so we can copy it from Ubuntu, it is attached [here](./tools/BEViewer.jar) for your convenience.

```batch
java  -jar c:\dftools\BEViewer.jar
```

## Demo video:
* Fall 2021
  * [Build two digital forensic platforms](https://youtu.be/rDyYYTl9X-0)
  * [Install Windows server 2022 on VirtualBox 6](https://youtu.be/qZ-ak9cl7GU)
* Fall 2020
  * [Build a digital forensic platform with Ubuntu 20.04](https://youtu.be/vU9Yqfh6PUE)
  * [Build a digital forensic platform with Windows server 2019](https://youtu.be/iVIQ1JGI8nQ)


## References:
* [Popular Computer Forensics Top 21 Tools](https://resources.infosecinstitute.com/computer-forensics-tools)
* [Ubuntu](https://ubuntu.com)
* [Kali Linux](https://www.kali.org)
* [CAINE Linux](https://www.caine-live.net)
* [Parrot Linux](https://parrotlinux.org/)
* [WineHQ](https://www.winehq.org/)
* [SDKMan](https://sdkman.io/)
* [How to completely uninstall Java?](https://askubuntu.com/questions/84483/how-to-completely-uninstall-java)
* [Linux: Problems using Autopsy on Kali](https://github.com/sleuthkit/autopsy/issues/3845)
* [VirtualBox.](https://www.virtualbox.org/)
* [autopsy: Running Linux OSX](https://github.com/sleuthkit/autopsy/blob/develop/Running_Linux_OSX.txt)
* [Sleuthkit & Autopsy](https://www.sleuthkit.org/)
* [hashdb](https://github.com/NPS-DEEP/hashdb/)
  * [hashdb](http://downloads.digitalcorpora.org/downloads/hashdb/)
* [Bulk extractor](http://downloads.digitalcorpora.org/downloads/bulk_extractor/)
* [Popular hex editors](https://www.ubuntupit.com/best-linux-hex-editor-top-20-linux-hex-viewers-editors/)
* [VMWare Workstation player](https://www.vmware.com/products/workstation-player.html)
  * [How to Convert VHD to VMDK: A Step-By-Step Guide](https://www.nakivo.com/blog/how-to-convert-vhd-to-vmdk-a-step-by-step-guide/)
  * [VMDK to VDI and VDI to VMDK in Windows](https://www.sysprobs.com/vmdk-vdi-windows)
* [Converting between image formats](https://docs.openstack.org/image-guide/convert-images.html)
* [How To Convert VirtualBox Disk Image (VDI) and img to Qcow2 format](https://computingforgeeks.com/how-to-convert-virtualbox-disk-image-vdi-and-img-to-qcow2-format/)
