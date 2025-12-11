# Fase 1: Preparació de l'entorn
Primer de tot haurem de configurar las xarxes de les dues màquines.
![](img/1.png)

![](img/2.png)

![](img/3.png)

![](img/4.png)

En el procés d'instal·lació de la màquina del server hem d'habilitar l'opció d'instal·lar el OpenSSH.
![](img/5.png)

Seguidament, instal·lem el SSH en la màquina de client.
```
sudo apt install ssh
```
![](img/6.png)

Mirem que vagin el les dues màquines.
```
ping 127.0.0.1
```

![](img/7.png)

```
ping 127.0.0.1
```
![](img/8.png)

I per acabar la fase 1 actualitzem les dues màquines.
```
sudo apt upgrade && sudo apt update
```

![](img/9.png)

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



![](img/15.png)

```
cd /srv
sudo mkdir /nfs
sudo mkdir /nfs/devs_projectes
```

![](img/16.png)

```
sudo mkdir /nfs/admin_tools
```

![](img/17.png)

```
cd /nfs
sudo chown root:devs dev_projectes
sudo chown root:admins admin_tools
```

![](img/18.png)

```
sudo chmod 770 dev_projectes
sudo chmod 770 admin_tools
```

![](img/19.png)

```
sudo apt install nfs-kernel-server -y
```

![](img/20.png)



![](img/21.png)

```
systemctl status nfs-server
```

![](img/22.png)

```
sudo nano /etc/exports
```

![](img/23.png)

```
/srv/nfs *(rw,sunc,no_subtree_check)
```

![](img/24.png)

```
sudo systemctl restart nfs-kernel-server
```

![](img/25.png)

```
sudo exportfs -u
```

![](img/26.png)

```
ip a
```

![](img/27.png)

```
sudo rpcinfo -p 192.168.56.105
```

![](img/28.png)

```
sudo apt install nfs-common -y
```

![](img/29.png)

```
sudo showmount -e 192.168.56.105
```

![](img/30.png)

```

```

![](img/31.png)

```

```

![](img/32.png)

```

```

![](img/33.png)

```

```

![](img/34.png)

```

```

![](img/35.png)

```

```

![](img/36.png)

```

```

![](img/37.png)

```

```

![](img/38.png)

```

```

![](img/39.png)

```

```

![](img/40.png)

![](img/41.png)

![](img/42.png)

![](img/43.png)

![](img/44.png)

![](img/45.png)

![](img/46.png)

![](img/47.png)

![](img/48.png)

![](img/49.png)

![](img/50.png)

![](img/51.png)

![](img/52.png)

![](img/53.png)

![](img/54.png)

![](img/55.png)

![](img/56.png)

![](img/57.png)

![](img/58.png)

![](img/59.png)

![](img/60.png)

![](img/61.png)

![](img/62.png)

![](img/63.png)

![](img/64.png)

![](img/65.png)

![](img/66.png)

![](img/67.png)

![](img/68.png)

![](img/69.png)

![](img/70.png)

![](img/71.png)

![](img/72.png)

![](img/73.png)

![](img/74.png)

![](img/75.png)

![](img/76.png)

![](img/77.png)

![](img/78.png)

![](img/79.png)

![](img/80.png)

![](img/81.png)

![](img/82.png)

![](img/83.png)

![](img/84.png)

![](img/85.png)

![](img/86.png)

![](img/87.png)

![](img/88.png)

![](img/89.png)

![](img/90.png)

![](img/91.png)

![](img/92.png)

![](img/93.png)

![](img/94.png)

![](img/95.png)

![](img/96.png)

![](img/97.png)

![](img/98.png)

![](img/99.png)

![](img/100.png)
