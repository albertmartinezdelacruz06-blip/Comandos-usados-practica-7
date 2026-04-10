# Comandos-usados-practica-7[comandos laboratorio 7.txt](https://github.com/user-attachments/files/26636422/comandos.laboratorio.7.txt)
comandos laboratorio 7 

sudo apt update
sudo apt install nfs-kernel-server -y

o
sudo mkdir -p /srv/OS3


for i in {1..100}; do sudo touch /srv/OS3/Adrian$i.txt; done


sudo chown -R nobody:nogroup /srv/OS3
sudo chmod -R 777 /srv/OS3

sudo nano /etc/exports

/srv/OS3  *(rw,sync,no_subtree_check)

sudo exportfs -ra
sudo systemctl restart nfs-kernel-server

sudo apt update
sudo apt install nfs-common -y

sudo mkdir -p /mnt/nfs_cliente
sudo mount [IP_DEL_SERVIDOR]:/srv/OS3 /mnt/nfs_cliente

sudo nano /etc/fstab

[192.168.7.219]:/srv/OS3  /mnt/nfs_cliente  nfs  defaults,_netdev  0  0

df -h | grep nfs
