Primer de tot en les dos maquines, posem la primera xarxa en Nat i la segona en Adaptador de només l’amfitrió. 

![](img/01.png)
![](img/02.png)

Seguidament, haurem d’editar el netplan tal com queda a la captura.

![](img/03.png)
![](img/04.png)
![](img/05.png)

Després instal·lem el SSH.

![](img/06.png)

Habilitem el servei.

![](img/07.png)

El reiniciem.

![](img/08.png)

I comprovem que estigui activat i funcionant.

![](img/09.png)

Seguidament, fem ip a per veure la nostre ip.

![](img/10.png)

Per poder connectar la màquina d’Ubuntu amb la de Windows (client), en el PowerShell de Windows posem SSH usuari@ (la IP que ens ha sortit en “IP a”) per connectar-nos entre màquines.

![](img/11.png)
![](img/12.png)

Confirmem que s’hagi connectat a la nostre màquina.

![](img/13.png)

Seguidament, posem una contrasenya al root.

![](img/14.png)

Després editarem el següent arxiu.

![](img/15.png)

Editant aquesta última línea (dos abaix del text que estava ja posat).

![](img/16.png)

Ara, iniciarem el root amb la màquina local.

![](img/17.png)

Comprovem que des de Windows ens denega l’accés (és el que hem configurat en l'anterior arxiu).

![](img/18.png)

Ara, amb aquesta comanda posarem dos codis rsa.

![](img/19.png)

Fem ls per mirar que tinguem les comandes. 

![](img/20.png)
![](img/21.png)

Seguidament, crearem un arxiu dins de la carpeta de ssh.

![](img/22.png)

Ara copiem el id_rsa.pub.

![](img/23.png)

Després mirem que en deixi entrar sense contrasenya.

![](img/24.png)

Seguidament, per posar el OpenSSH anem a configuració a sistema a característiques opcionals.

![](img/25.png)

Ara a ver carecterísticas i ens sortiran les característiques que podem agregar.

![](img/26.png)

I si cliquem al text blau de l’anterior captura, afegim el OpenSSH.

![](img/27.png)
![](img/28.png)

Ara per desactivar el firewall obrirem aquesta aplicació.

![](img/29.png)

Ara anem dins de anem a l’apartat de Firewall

![](img/30.png)

I desactivar el firewall de microsoft defender.

![](img/31.png)

Ara per poder iniciar el ssh obrim el powershell com a administrador.

![](img/32.png)

Fem aquestes scripts per iniciar el ssh.

![](img/33.png)
![](img/34.png)

Confirmem que s’ha activat.

![](img/35.png)

Ara a ubuntu confirmem que vagi la connexió.

![](img/36.png)
![](img/37.png)
![](img/38.png)

Ara per fer el túnel connectem el ssh.

![](img/39.png)

Seguidament per configurar el proxy entrarem al panel de control, a redes e interned.

![](img/40.png)

Dins a opciones de interned.

![](img/41.png)

I a configurar de LAN.

![](img/42.png)

Ara habilitarem el servidor proxy.

![](img/43.png)

Posant el local ip i el port (en aquest cas el 9876), podriem posar alguns altres. Un cop configurat li donem a aceptar a tot.

![](img/44.png)

I per últim dins de wireshark mirem que el tunel funcioni.

![](img/45.png)

