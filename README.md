# QEMUDebian - ARM

If you want to emulate `cortex-a9` CPU and `vexpress-a9` machine (ARMv7 CPU which Debian calls as `armhf` (ARM hard float)). You must download vmlinuz and initrd files.

This repository generates all the files required for emulating all ARMv7 CPUs (Cortex-A8, A9, A15) and ARM64.

Download `vmlinuz`, `initrd` and `qcow2` images from the release page and start your virtual machine with QEMU:

```
qemu-system-arm -m 512 -kernel ./vmlinuz-5.10.0-20-armmp \
                -initrd ./initrd.img-5.10.0-20-armmp \
                -append "console=ttyAMA0 debug root=/dev/sda net.ifnames=0" \
                -hda ./bullseye-armhf-armmp.qcow2 -nographic \
                -nic user,model=virtio-net-pci,hostfwd=tcp::5555-:22
```

Per default two users are created:

1. root:root
2. sensys:sensys
