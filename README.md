# HackintoshVectrasVM
This Is A Guide On How To Emulate MacOS On Andriod With VectrasVM
# Requirements
A Galaxy Note 5, Galaxy S7 Or Newer. A Andriod Phone That Was Released In 2016 Till Present.

At Least 4GB RAM

At Least 128GB Storage

At Least 4 CPU Cores

VectrasVM Andriod [Vectras-VM-Andriod](https://github.com/xoureldeen/Vectras-VM-Android/releases/tag/v2.9.5)

OpenCore QCOW2 Image (You Cannot Choose Another File From Another Source, Or MacOS Wont Boot!) [OpenCore](https://github.com/Coopydood/ultimate-macOS-KVM/blob/main/resources/oc_store/compat_new/OpenCore.qcow2)

OVMF BIOS [EDK2](https://github.com/clearlinux/common/blob/master/OVMF.fd)

OVMF Variables [Ovmf Vars](https://github.com/clearlinux/common/blob/master/OVMF_VARS.fd)

MacOS ISO (You Cannot Choose Another ISO, Or The Mouse Wont Work!) [MacOS ISO](https://archive.org/details/macos-collection)

MacOS QCOW2 Drive (Use This To Install MacOS On) [MacOS QCOW2 Drive](https://www.mediafire.com/file/gz9ordqm51a7v8p/macos.qcow2/file)

# VectrasVM Setup

Create A New Virtual Machine By Tapping On The "+" Button

Add And Modify This Template Text To The QEMU Params

-M pc-q35-8.2,nvdimm=on -usb -device usb-tablet -device usb-kbd -cpu SandyBridge-IBRS,vendor=GenuineIntel,kvm=on,+vmx,vmware-cpuid-freq=on,+invtsc,+hypervisor,+avx,+sse3,+sse4.2 -smp sockets=1,cores=2,threads=2 -m 2048M -drive file=/storage/emulated/0/yourpathto/OpenCore.qcow2,aio=threads,cache=writeback -drive file="/storage/emulated/0/yourpathto/TargetVolume.qcow2",aio=threads,cache=writeback -device vmware-svga,vgamem_mb=128 -device intel-hda -device hda-duplex -device intel-iommu -device rtl8139,netdev=n0 -netdev user,id=n0 -drive if=pflash,format=raw,unit=0,file=/storage/emulated/0/yourpathto/OVMF/OVMF_CODE.fd,readonly=on -drive if=pflash,format=raw,unit=1,file=/storage/emulated/0/yourpathto/OVMF/OVMF_VARS.fd,readonly=on -device isa-applesmc,osk=ourhardworkbythesewordsguardedpleasedontsteal\(c\)AppleComputerInc -device virtio-gpu-pci -device virtio-balloon-pci -device virtio-serial-pci -device virtio-rng-pci -device virtio-net-pci -accel tcg,thread=multi,tb-size=2048 -smbios type=2 -drive index=3,media=cdrom,file=/storage/emulated/0/yourpathto/macosinstaller.iso

Change "/storage/emulated/0/yourpathto/TargetVolume.qcow2" To The MacOS Target System Path (macos.qcow2 that you downloaded from mediafire)

Change "/storage/emulated/0/yourpathto/OVMF/OVMF_CODE.fd" To Your Path To The OVMF.fd File

Change "/storage/emulated/0/yourpathto/OVMF/OVMF_VARS.fd" To Your Path To The OVMF_VARS.fd File

Change "/storage/emulated/0/yourpathto/macosinstaller.iso" To Your Path To The MacOS Installer ISO Image

Save The Changes

Tap On The VM

When Booted Into OpenCore, Click On "Install MacOS"

Wait For MacOS To Boot (this may take a while)

When You Get A Chance, Go To Disk Utility. Erase The QEMU Harddisk That Has 128GB On It

When Erased, Exit And Setup MacOS

Agree To The Terms And Conditions, Then Install MacOS To The Harddisk

Wait For It To Boot Into OpenCore Again, Then Go To MacOS Installation
