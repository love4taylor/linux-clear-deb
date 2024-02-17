# Clearlinux kernel for Debian

Based on the Debian generic kernel configuration file

## Installation

```shell
# You need to install curl, wget and jq first.
wget $(curl -s https://api.github.com/repos/love4taylor/linux-clear-deb/releases/latest  | jq -r '.assets[] | select(.name | contains ("deb")) | .browser_download_url')
sudo dpkg -i linux-headers-*.deb
sudo dpkg -i linux-image-*.deb
sudo dpkg -i linux-libc-dev_*.dev #optional
# Then reboot
```

## Patchs

- [Clear Linux Patchs](https://github.com/clearlinux-pkgs/linux) (Exclude 0132, 0118, 0113, 0138, 0139)

## Notice

1. It is recommended to add `quiet console=tty0 console=ttyS0,115200n8 cryptomgr.notests initcall_debug intel_iommu=igfx_off kvm-intel.nested=1 no_timer_check noreplace-smp page_alloc.shuffle=1 rcupdate.rcu_expedited=1 rootfstype=ext4,btrfs,xfs,f2fs tsc=reliable rw` to the boot cmdline if you are using an **Intel** CPU.
