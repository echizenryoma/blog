# VMware Worksation

## Windows虚拟机

### 1. 图像渲染问题

#### 问题

![Windows 10虚拟机显示问题](https://scontent-nrt1-2.cdninstagram.com/v/t51.2885-15/482051855_17898114708120530_2430210207834297915_n.jpg?stp=dst-jpg_e15_tt6&efg=eyJ2ZW5jb2RlX3RhZyI6ImltYWdlX3VybGdlbi45NjR4NjM1LnNkci5mNzU3NjEuZGVmYXVsdF9pbWFnZSJ9&_nc_ht=scontent-nrt1-2.cdninstagram.com&_nc_cat=102&_nc_oc=Q6cZ2AEwHACaewAf3i36xGInZ5349WlVpIchnXMelyjefKtr6VPy42SVEiBYQXIXD3qyDEM&_nc_ohc=FctlNOJO4KMQ7kNvgGhEY-k&_nc_gid=e5cc112406e24da0b6db09d0998e5e30&edm=APs17CUBAAAA&ccb=7-5&ig_cache_key=MzU3NzA5ODQ3ODE0MTYyNzU4Nw%3D%3D.3-ccb7-5&oh=00_AYDvsDOrELsRMcn0azX2lbIV84-IvQ0FMdldpnNja-Q-eg&oe=67CA3772&_nc_sid=10d13b)

表现为随机的撕裂，周期卡死的情况

#### 解决方案

修改vmx文件，将`mks.enableDX12Presentation=FALSE` 添加到 vmx 配置文件中

#### 参考

1. [Windows 11 Guest freezes in Workstation 17.6](https://community.broadcom.com/vmware-cloud-foundation/question/windows-11-guest-freezes-in-workstation-176)
2. [Anyone experiencing strange graphical issues in VMware? 🥴](https://www.threads.net/@thebobpony/post/DGkaB0UONzD/anyone-experiencing-strange-graphical-issues-in-vmware-)
