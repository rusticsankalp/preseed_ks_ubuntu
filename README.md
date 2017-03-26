# preseed_ks_ubuntu
collection of scripts for automating linux server install 

primary source http://gyk.lt/ubuntu-14-04-desktop-unattended-installation/

1. compare and place txt.cfg in /isolinux
2. copy ks.cfg to / 
3. copy ubuntu-server.seed in /preseed
4. mkdir /custom
 4.1 copy id_rsa and id_rsa.pub to /custom
 
 Useful commands 
 -----
mkdir ubuntu_iso
sudo mount -o loop ~/Downloads/ubuntu-14.04.3-server-i386.iso ubuntu_iso

mkdir ubuntu_files
sudo rsync -a ubuntu_iso/ ubuntu_files/
sudo chmod -R 755 ubuntu_files
sudo chown -R ernestas:ernestas ubuntu_files

cd ubuntu_files
mkisofs -D -r -V “ubuntu-auto” -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ~/Desktop/ubuntu-auto.iso .

 
 
