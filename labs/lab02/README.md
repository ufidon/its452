# its452
course materials and references for its452

## lab02: Disk partition

**1. Objectives**

* Practice on two popular drive partition schemes: [MBR](https://en.wikipedia.org/wiki/Master_boot_record) and [GPT](https://en.wikipedia.org/wiki/GUID_Partition_Table)
* Be able to describe MBR and GPT
* Analyze MBR and GPT manually

**2. Tasks**

*It is fine if your partition sizes, types are different from the figures below, but the number of partitions should be the same as the figures.*

1. (10%) Use dd command to create two disk images each of size 500M and filled with zero
2. (10%) Use losetup to mount these two disk images to two loop devices
3. (40%) *With MBR as the partition scheme*, use GParted to partition the first image into partitions as ![image1 partitions](./demo/image1.png). 
   1. (10%) Unmount the image, explore the partitions with sleuthkit image file tools(img_stat) and volume system tools(mmls)
   2. (30%) Mount the image with losetup, explore the partitions with wxHexEditor, identify the information shown with mmls inside wxHexEditor.
   3. (Optional) *show the link list of EBR*, here is a [demo](./demo/AnalyzingEBR.pdf)
4. (40%) *With GPT as the partition scheme*, use gdisk to partition the second image into 5 partitions as ![image2 partitions](./demo/image2.png)
   1. (10%) Unmount the image, explore the partitions with sleuthkit image file tools (img_stat) and volume system tools(mmls) 
   2. (30%) Mount the image with losetup, explore the partitions with wxHexEditor, identify the information shown with mmls inside wxHexEditor.

**3. Tools**

* [dd](https://en.wikipedia.org/wiki/Dd_(Unix))
* _file split and concatenation_
  * [split](https://en.wikipedia.org/wiki/Split_(Unix))
  * [cat](https://en.wikipedia.org/wiki/Cat_(Unix))
* [wxHexEditor](https://www.wxhexeditor.org/)
  * [wxhexeditor](../../lectures/module02/wxhexeditor.md)
* [fdisk](https://tldp.org/HOWTO/Partition/fdisk_partitioning.html)
  * [gdisk](http://www.rodsbooks.com/gdisk/)
* [GParted](https://en.wikipedia.org/wiki/GParted)
  * [GNOME Partition Editor](https://gparted.org/)
* [Loop device](https://en.wikipedia.org/wiki/Loop_device)
  * [losetup](https://man7.org/linux/man-pages/man8/losetup.8.html)
  * [How to use loop devices](https://blog.sleeplessbeastie.eu/2017/07/03/how-to-use-loop-devices/)
* [sleuthkit](https://www.sleuthkit.org/sleuthkit/)
  * [wiki](http://wiki.sleuthkit.org)
  * [doc](http://wiki.sleuthkit.org/index.php?title=Help_Documents)
  * [TSK Tool Overview](http://wiki.sleuthkit.org/index.php?title=TSK_Tool_Overview)
  * [Implementation doc](http://wiki.sleuthkit.org/index.php?title=Design_Documents)
  * [source code](https://github.com/sleuthkit/sleuthkit)

**4. Demo videos**

* _2020 Fall_
  * [Lab02 Part 1: DiskPartitioning](https://youtu.be/HviukcJQBuQ)
  * [Lab02 Part 2: DiskPartitioning](https://youtu.be/GSGi42YGUco)

**References:**
* [Disk partition](https://en.wikipedia.org/wiki/Disk_partitioning)
  * [Partition Table](https://wiki.osdev.org/Partition_Table)
* [MBR](https://en.wikipedia.org/wiki/Master_boot_record)
  * [Master Boot Record (MBR)](https://wiki.osdev.org/MBR_(x86))
* [GPT](https://en.wikipedia.org/wiki/GUID_Partition_Table)
  * [GUID Partition Table](https://wiki.osdev.org/GPT)
* [How to install an Operating System (OS) using the GUID Disk Partition Table (GPT)](./refs/gptwhitepaper11.pdf)
* [Apple partition map](https://en.wikipedia.org/wiki/Apple_Partition_Map)

