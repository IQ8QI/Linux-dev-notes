# Installing new kernel from source
## Getting packages required for the work
Packages to only compile
```
sudo apt install libncurses5-dev gcc make git exuberant-ctags bc libssl-dev libelf-dev
```

Packages to compile and commit to development
```
sudo apt-get install vim libncurses5-dev gcc make git exuberant-ctags libssl-dev bison flex libelf-dev bc dwarves zstd git-email
```
## Getting kernel source
### Fetching sources
Stable Sources
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
```
Staging sources
```
git clone -b staging-testing https://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging.git
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
Coping configuration from current system
```
cp /boot/config-`uname -r`* .config
```

Setting default values for the new configs not present in previous config
```
make olddefconfig
```

Enabling default configuration
It usually is a bad idea, unless You are maybe in virtual machine
```
make defconfig
```

Manually configure kernel
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
### Automatic Install:
```
sudo make modules_install install
```

### Some steps of manual install (not complete)
Adding new kernel to grub2
```
sudo update-grub2
```

Creating new initial ram disk for new kernel
```
sudo update-initramfs -c -k 6.5.6
```
