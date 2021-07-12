# VM-INSTALLATION
# First open the Terminal
# Type following commands.
## 1. Download the latest arm disk image to $HOME:https://dl.fedoraproject.org/pub/fedora/linux/releases/32/Spins/armhfp/images/Fedora-Minimal-armhfp-32-1.6-sda.raw.xz
## 2. Extract the disk image: unxz Fedora-Minimal-armhfp-32-1.6-sda.raw.xz
## 3. Install virt-builder: sudo dnf install libguestfs-tools-c
## 4.Extract the kernel/initrd from the disk image: virt-get-kernel -a Fedora-Minimal-armhfp-32-1.6-sda.raw
## 5. Get kernel args for the the image: virt-cat -a Fedora-Minimal-armhfp-32-1.6-sda.raw /etc/extlinux.conf
## 6. Copy the media to the the default libvirt image location: sudo mv Fedora-Minimal-armhfp-32-1.6-sda.raw vmlinuz-*.armv7hl initramfs-*.armv7hl.img /var/lib/libvirt/images/
## 7. Ensure qemu-system-arm is installed: sudo get install qemu-system-arm
## 8. sudo virt-install \ 
    --name fedora-armhfp-32 --ram 3072 --arch armv7l --machine virt-2.11 --os-variant fedora32 --import \
    --disk /var/lib/libvirt/images/fedora-armhfp-32.raw.1.6 \
    --boot kernel=/var/lib/libvirt/images/vmlinuz-5.6.6-300.fc32.armv7hl,initrd=/var/lib/libvirt/images/initramfs-5.6.6-300.fc32.armv7hl.img,kernel_args="console=ttyAMA0 rw root=LABEL=_/ rootwait"
## Link I used about this. https://michel-slm.name/posts/2020-08-20-fedora-armhfp-vm/
