# Installing new kernel from source
## Getting packages required for the work
```
sudo apt install libncurses5-dev gcc make git exuberant-ctags bc libssl-dev libelf-dev vim
```
## Getting kernel source
### Fetching sources
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
cd linux-stable
```
### Searching available kernel versions
```
git tag -l | less
```

### Chosing target version
```
git checkout -b stable tag
```
## Creating configuration
### Coping configuration from current system
```
cp /boot/config-`uname -r`* .config
```
###  Enabling default configuration
```
make defconfig
```
### Manually configure kernel
```
make menuconfig
```
## Compile choosen kernel version
Compile:
```
make
```
Compile with X cores:
```
make -jX
```
## Installing kernel
```
sudo make modules_install install
```
## Adding new kernel to grub2
```
sudo update-grub2
```
## Creating new initial ram disk for new kernel
```
sudo update-initramfs -c -k 6.5.6
```
