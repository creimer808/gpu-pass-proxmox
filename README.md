# gpu-pass-proxmox

   67  nano /etc/default/grub
   68  update-grub
   69  nano /etc/modules
   70  nano /etc/modules
   71  y
   72  echo "options vfio_iommu_type1 allow_unsafe_interrupts=1" > /etc/modprobe.d/iommu_unsafe_interrupts.conf
   73  echo "options kvm ignore_msrs=1" > /etc/modprobe.d/kvm.conf
   74  echo "blacklist radeon" >> /etc/modprobe.d/blacklist.conf
   75  echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
   76  echo "blacklist nvidia" >> /etc/modprobe.d/blacklist.conf
   77  lspci -v
   78  lspci -n -s 04:00
   79  echo "options vfio-pci ids=10de:1c30,10de:10f1 disable_vga=1"> /etc/modprobe.d/vfio.conf
   80  update-initramfs -u
