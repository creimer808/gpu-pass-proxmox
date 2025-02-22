# GPU Pass-Through for Proxmox

```sh
nano /etc/default/grub  
update-grub  
nano /etc/modules  
nano /etc/modules  
y  
echo "options vfio_iommu_type1 allow_unsafe_interrupts=1" > /etc/modprobe.d/iommu_unsafe_interrupts.conf  
echo "options kvm ignore_msrs=1" > /etc/modprobe.d/kvm.conf  
echo "blacklist radeon" >> /etc/modprobe.d/blacklist.conf  
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf  
echo "blacklist nvidia" >> /etc/modprobe.d/blacklist.conf  
lspci -v  
lspci -n -s 04:00  
echo "options vfio-pci ids=10de:1c30,10de:10f1 disable_vga=1" > /etc/modprobe.d/vfio.conf  
update-initramfs -u  
