# VMware Fusion

## Windows 11 arm64

### 驱动缺失

#### 1. Base System Device

##### 硬件ID

PCI\VEN_15AD&DEV_0740&SUBSYS_074015AD&REV_10
PCI\VEN_15AD&DEV_0740&SUBSYS_074015AD
PCI\VEN_15AD&DEV_0740&CC_088000
PCI\VEN_15AD&DEV_0740&CC_0880

##### 解决方案

修改vmx文件，将`vmci0.present = "TRUE"`修改为`vmci0.present = "FALSE"`

#### 2. Universal Serial Bus (USB) Controller

##### 硬件ID

PCI\VEN_15AD&DEV_0774&SUBSYS_197615AD&REV_00
PCI\VEN_15AD&DEV_0774&SUBSYS_197615AD
PCI\VEN_15AD&DEV_0774&CC_0C0300
PCI\VEN_15AD&DEV_0774&CC_0C03

##### 问题原因

微软已取消Windows ARM的内置EHCI驱动程序

##### 解决方案

vmx文件增加`usb.uhci.present = "FALSE"`

### 参考

1. [Windows 11 ARM device manager shows yellow exclamation for VMCI Bus Device and USB2 EHCI controller ](https://community.broadcom.com/communities/community-home/digestviewer/viewthread?GroupId=7165&MessageKey=a4a28351-1910-4aac-88dc-2f5d02752b31&CommunityKey=0c3a2021-5113-4ad1-af9e-018f5da40bc0)
