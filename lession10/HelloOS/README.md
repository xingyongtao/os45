# 10 | 设置工作模式与环境（上）：建立计算机

运行`make`命令即可查看HelloOS引导过程。

```bash
make
```

## 1. 生产虚拟硬盘

### 1.1 alpine
```
# losetup --help
BusyBox v1.33.1 () multi-call binary.

Usage: losetup [-rP] [-o OFS] {-f|LOOPDEV} FILE: associate loop devices
	losetup -c LOOPDEV: reread file size
	losetup -d LOOPDEV: disassociate
	losetup -a: show status
	losetup -f: show next free loop device

	-o OFS	Start OFS bytes into FILE
	-P	Scan for partitions
	-r	Read-only
	-f	Show/use next free loop device
```

### 1.2 ubuntu

查看最新可用的设备
```
losetup -f
```

设置
```
sudo losetup -f hd.img
```

检查是否成功
```
losetup
```
或者
```
losetup -a
```

格式化
```
sudo mkfs.ext4 -q /dev/loop1
```

挂载并创建目录
```
mkdir hdisk
sudo mount -o loop ./hd.img ./hdisk/
sudo mkdir ./hdisk/boot/
```

## 2. 安装 GRUB

```
$ sudo grub-install --boot-directory=./hdisk/boot/ --force --allow-floppy /dev/loop1
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
```

## 3. 效果展示

在ubuntu宿主机(Host)上做出来的镜像，可以使用Docker运行，macOS（M1芯片/ARM64）也可以运行。

出现HelloOS的错误提示后，如果继续按回车，会继续回到之前的选择界面，再按`c`会取消并进入命令行，这个时候再输入`halt`就关掉虚拟机了。