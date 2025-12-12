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
Primer de tot creem dos grups.
```
sudo groupadd devs
sudo groupadd admins
```

![](img/11.png)

Desprès creem dos usuaris i els hi posem al grup corresponent.
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

Els creem a la màquina del client.

![](img/14.png)

Dins de srv crearem la carpeta nfs i dins d'ella la dev_projectes.
```
cd /srv
sudo mkdir /nfs
sudo mkdir /nfs/devs_projectes
```

![](img/15.png)

També el admin_tools.
```
sudo mkdir /nfs/admin_tools
```

![](img/16.png)

Els hi donem els permisos de root.
```
cd /nfs
sudo chown root:devs dev_projectes
sudo chown root:admins admin_tools
```

![](img/17.png)

També posem els permisos 2775. Tot això també ho fem a l'altre màquina de forma gràfica.
```
sudo chmod 770 dev_projectes
sudo chmod 770 admin_tools
```

![](img/18.png)

Seguidament instalem el nfs kernel server.
```
sudo apt install nfs-kernel-server -y
```

![](img/19.png)



![](img/20.png)

Mirem que estigui activat.
```
systemctl status nfs-server
```

![](img/21.png)

I configurem el arxiu exports.
```
sudo nano /etc/exports
```

![](img/22.png)

Posant aquest text.
```
/srv/nfs *(rw,sunc,no_subtree_check)
```

![](img/23.png)

I apliquem el canvï resetejant el sistema.
```
sudo systemctl restart nfs-kernel-server
```

![](img/24.png)


```
sudo exportfs -u
```


![](img/25.png)

Ara farem ip a per mirar la ip que tenim per la següent captura.
```
ip a
```

![](img/26.png)

Ara amb la ip d'abans fem aquesta comanda per mirar si funciona.
```
sudo rpcinfo -p 192.168.56.105
```

![](img/27.png)

Seguidament per connectar el client desde el Zorin instal·lem aquests paquets.
```
sudo apt install nfs-common -y
```

![](img/28.png)

I ho connectem fent servir la ip d'abans.
```
sudo showmount -e 192.168.56.105
```

![](img/29.png)

# Fase 3: L'Exportació d'Administració (El Dilema del root_squash)
## Prova 1 (error)
En aquesta fase intentem crear un fitxer dins del directori.
```
sudo mkdir /mnt/admin_tools
```

![](img/30.png)

```
sudo mount -t nfs 192.168.56.105:/srv/nfs/admin_tools /mnt/admin_tools
```

![](img/31.png)

I observem que com abans hem posat no tenim els permisos per entrar a la carpeta.

![](img/32.png)
![](img/33.png)

Verificar quin és el propietari del fitxer creat. Per què? Justificar la resposta amb l'explicació tècnica de 'root_squash'.

No podem accedir a la carpeta perquè no tenim els permisos que necessitem. Això passa perquè no està activat el root squash, que fa que l'usuari amb privilegis de la màquina client no sigui reconegut com el root del servidor.

---
Iniciem sessió en admin01.
```
sudo login admin01
```

![](img/34.png)

```
bash
```

![](img/35.png)

Dins de admin01 creem la file01
```
touch /mnt/admin_tools/file01
```

![](img/36.png)

I mirem que estigui bé.
```
ls -l /mnt/admin_tools
```

![](img/37.png)

## Prova 2 (solució)
Editarem el exports
```
sudoi nano /etc/exports
```

![](img/38.png)

D'aquesta forma.
```
/srv/nfs/admin_tools *(rw,sync,no_subtree_check,no_root_squash)
/srv/nfs/dev_projectes *(rm,syn,no_subtree_check)
```

![](img/39.png)

Resetajem el sistema.
```
sudo systemctl restart nfs-kernel-server
```

![](img/40.png)

Desmontem i tornem a montar el recurs.
```
sudo umount /mnt/admin_tools
sudo mount 192.168.56.105:/srv/nfs/admin_tools /mnt/admin_tools
```

![](img/41.png)

I com a root intentem crear un fitxer dins del directori muntat i mirem quin es el propietari del fitxer.
```
sudo su root
touch /mnt/admin_tools/file02
ls /mnt/admin_tools/
ls -l /mnt/admin_tools/
```

![](img/42.png)

# Fase 4:

Editem el exports.
```
sudo nano /etc/exports
```

![](img/43.png)

D'aquesta forma.
```
/srv/nfs/admin_tools *(rw,sync,no_subtree_check,no_root_squash)
/srv/nfs/dev_projectes 192.168.56.0/24(rm,syn,no_subtree_check)
/srv/nfs/dev_projectes 192.168.56.140(ro,sync,no_subtree_check)
```

![](img/44.png)

El resetajem.
```
sudo systemctl restart nfs-kernel-server
```

![](img/45.png)

I creem aquesta carpeta.
```
sudo mkdir /mnt/dev_projectes
```

![](img/46.png)

Editem la xarxa per mirar si funciona, en aquest cas la 8.

![](img/47.png)

I creem aquesta.

![](img/48.png)

I ho montem.
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

Ara per desmuntar-ho canviem la ip.

![](img/53.png)



![](img/54.png)

I mirem si podem escriure al directori
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

I mirem que en deixi només llegir.
```
touch /mnt/dev_projectes/file06
```

![](img/57.png)

# Fase 5:
Per ùltima fase editem el següent fitxer per poder afegir entrades als recursos compartits NFS al directori següent.
```
sudo nano /etc/fstab
```

![](img/58.png)

```
192.168.56.105:/srv/nfs/admin_tools /mnt/admin_tools nfs defaults 0 0
192.168.56.105:/srv/nfs/dev_projectes /mnt/dev_projectes nfs defaults 0 0
```

![](img/59.png)

Reiniciem la màquina i mirem que els recursos compartits s'hagin montat bé.
```
sudo su root
cd
cd /media
ls -l /mnt/
```

![](img/60.png)

---
# Conclusió i Recomanacions
El sistema NFS funciona bé per compartir carpetes entre servidor i client si es configura correctament. Hem vist que els permisos i el fitxer /etc/exports són claus, i que el root_squash evita que el root del client tingui control total, cosa que és important per seguretat.
### Recomanacions:

- Deixar root_squash activat per evitar riscos, excepte en xarxes molt segures.
- Configurar bé permisos i grups abans de compartir carpetes.
- Usar IPs fixes per controlar qui té accés i amb quins permisos.
- Afegir les entrades a /etc/fstab per muntatge automàtic.
- Fer còpies de seguretat abans de canvis importants.
