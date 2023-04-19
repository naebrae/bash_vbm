# VirtualBox Manage

Bash script to help create virtualbox images. The examples provided are for Red Hat Server vagrant boxes.

## Requirements

- virtualbox
- syslinux
- genisoimage

> Optional
- vagrant

## Usage

This works by creating a minimal boot image with the build kickstart file. 'inst.stage2' is used from the original Red Hat ISO so the minimal boot image needs to match the original ISO. The bash script 'mkisolinux' (included) copies the required files from the original ISO to the folder used to create the boot image. A kickstart file is required (samples provided).

After the boot image folder is complete, the included 'build' script along with the configuration file samples automate the build the virtualbox image. If vagrant is installed, a vagrant box can be created (configuration option EXPORT=0) or a virtualbox virtual applicance can be created (configuration option EXPORT=1). The build script builds EFI images but BIOS images are also supported.

> These create EFI based images
```
cd boxes
../bin/mkisolinux -e ~/isos/rhel-server-7.9-x86_64-dvd.iso rhelsrv7.9
../bin/mkisolinux -e ~/isos/rhel-8.6-x86_64-dvd.iso rhelsrv8.6
../bin/mkisolinux -e ~/isos/rhel-baseos-9.1-x86_64-dvd.iso rhelsrv9.1
```

```
../bin/build rhel_7_9
../bin/build rhel_8_6
../bin/build rhel_9_1
```
