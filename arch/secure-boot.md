# UEFI安全启动

## 1. sbctl

### 1.1 准备

* 重新安装`grub`启动器

```shell
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=arch --modules="tpm" --disable-shim-lock
```

* 重新生成`grub`配置

```shell
grub-mkconfig -o /boot/grub/grub.cfg
```

* 安装`sbctl`

```bash
pacman -S sbctl
```

* UEFI设置

1. 进入UEFI管理
2. “安全”(Secure)-“安全启动”(Secure Boot)-“进入部署模式”(Reset to Setup Mode)
3. 关闭“安全启动”(Secure Boot)
4. 保存后重启

* 检查状态

```shell
sbctl status
```

确保处于部署模式

* 生成密钥

```shell
sbctl create-keys
```

* 注册密钥

```shell
sbctl enroll-keys -m
```

-m表示需要微软密钥

* 签名`grub`启动器

```shell
sbctl sign -s /boot/efi/EFI/arch/grubx64.efi
```

* 签名`linux`内核

```shell
sbctl sign -s /boot/vmlinuz-linux
```

* 验证签名

```shell
sbctl verify
```

* UEFI设置

1. 进入UEFI管理
2. 启用“安全启动”(Secure Boot)
3. 保存后重启

## 2. 参考

1. [My easy method for setting up Secure Boot with GRUB](https://www.reddit.com/r/archlinux/comments/10pq74e/my_easy_method_for_setting_up_secure_boot_with/)
2. [Unified Extensible Firmware Interface/Secure Boot](https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot)
