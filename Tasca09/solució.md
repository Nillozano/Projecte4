# Fase 1: Preparació de l'entorn
Primer de tot haurem de configurar las xarxes de les dues màquines.
![](img/01.png)

![](img/02.png)

![](img/03.png)

![](img/04.png)

En el procés d'instal·lació de la màquina del server hem d'habilitar l'opció d'instal·lar el OpenSSH.
![](img/05.png)

Seguidament, instal·lem el SSH en la màquina de client.
```
sudo apt install ssh
```
![](img/06.png)

Mirem que vagin el les dues màquines.
```
ping 127.0.0.1
```

![](img/07.png)

```
ping 127.0.0.1
```
![](img/08.png)

I per acabar la fase 1 actualitzem les dues màquines.
```
sudo apt upgrade && sudo apt update
```

![](img/09.png)

```
sudo apt upgrade && sudo apt update
```

![](img/10.png)

# Fase 2: Preparació del servidor

```
sudo groupadd devs
sudo groupadd admins
```

![](img/11.png)

```
sudo useradd dev01
sudo usermod -aG devs dev01
```

![](img/12.png)

```
sudo useradd admin01
sudo usermod -aG admins admin01
```

![](img/13.png)



![](img/14.png)

```
cd /srv
sudo mkdir /nfs
sudo mkdir /nfs/devs_projectes
```

![](img/15.png)


```
sudo mkdir /nfs/admin_tools
```

![](img/16.png)

```
cd /nfs
sudo chown root:devs dev_projectes
sudo chown root:admins admin_tools
```

![](img/17.png)

```
sudo chmod 770 dev_projectes
sudo chmod 770 admin_tools
```

![](img/18.png)

```
sudo apt install nfs-kernel-server -y
```

![](img/19.png)



![](img/20.png)

```
systemctl status nfs-server
```

![](img/21.png)

```
sudo nano /etc/exports
```

![](img/22.png)

```
/srv/nfs *(rw,sunc,no_subtree_check)
```

![](img/23.png)

```
sudo systemctl restart nfs-kernel-server
```

![](img/24.png)

```
sudo exportfs -u
```


![](img/25.png)

```
ip a
```

![](img/26.png)

```
sudo rpcinfo -p 192.168.56.105
```

![](img/27.png)

```
sudo apt install nfs-common -y
```

![](img/28.png)

```
sudo showmount -e 192.168.56.105
```

![](img/29.png)

# Fase 3: L'Exportació d'Administració (El Dilema del root_squash)

```
sudo mkdir /mnt/admin_tools
```

![](img/30.png)

```
sudo mount -t nfs 192.168.56.105:/srv/nfs/admin_tools /mnt/admin_tools
```

![](img/31.png)



![](img/32.png)



![](img/33.png)

```
sudo login admin01
```

![](img/34.png)

```
bash
```

![](img/35.png)

```
touch /mnt/admin_tools/file01
```

![](img/36.png)

```
ls -l /mnt/admin_tools
```

![](img/37.png)

```
sudoi nano /etc/exports
```

![](img/38.png)

```
/srv/nfs/admin_tools *(rw,sync,no_subtree_check,no_root_squash)
/srv/nfs/dev_projectes *(rm,syn,no_subtree_check)
```

![](img/39.png)

```
sudo systemctl restart nfs-kernel-server
```

![](img/40.png)

```
sudo umount /mnt/admin_tools
sudo mount 192.168.56.105:/srv/nfs/admin_tools /mnt/admin_tools
```

![](img/41.png)

```
sudo su root
touch /mnt/admin_tools/file02
ls /mnt/admin_tools/
ls -l /mnt/admin_tools/
```

![](img/42.png)

# Fase 4:

```
sudo nano /etc/exports
```

![](img/43.png)

```
/srv/nfs/admin_tools *(rw,sync,no_subtree_check,no_root_squash)
/srv/nfs/dev_projectes 192.168.56.0/24(rm,syn,no_subtree_check)
/srv/nfs/dev_projectes 192.168.56.140(ro,sync,no_subtree_check)
```

![](img/44.png)

```
sudo systemctl restart nfs-kernel-server
```

![](img/45.png)

```
sudo mkdir /mnt/dev_projectes
```

![](img/46.png)



![](img/47.png)



![](img/48.png)

```
sudo mount 192.168.56.105:/srv/nfs/dev_projectes /mnt/dev_projectes
```

![](img/49.png)

```
sudo login dev01
```

![](img/50.png)

```
cd /mnt/dev_projectes
touch file04
```

![](img/51.png)

```
ls
```

![](img/52.png)



![](img/53.png)



![](img/54.png)

```
sudo su root
cd /mnt/dev_projectes/
ls
```

![](img/55.png)

```
touch file05
```

![](img/56.png)

```
touch /mnt/dev_projectes/file06
```

![](img/57.png)

# Fase 5:

```
sudo nano /etc/fstab
```

![](img/58.png)

```
192.168.56.105:/srv/nfs/admin_tools /mnt/admin_tools nfs defaults 0 0
192.168.56.105:/srv/nfs/dev_projectes /mnt/dev_projectes nfs defaults 0 0
```

![](img/59.png)

```
sudo su root
cd
cd /media
ls -l /mnt/
```

![](img/60.png)

