# Installing new kernel from source
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


