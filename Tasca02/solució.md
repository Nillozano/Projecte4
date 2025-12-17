## Còpies de Windows
Primer de tot creem un segon disc per després posar les còpies de seguretat.

![](img/01.png)

Seguidament, posem el primer disc per posar el sistema operatiu (windows).

![](img/02.png)

Farem les còpies via duplicati, fem l’instal·lació. 

![](img/03.png)

Habil·litem el segon disc per poder després posar les còpies.

![](img/04.png)

Ara farem les còpies de seguretat.

![](img/05.png)
![](img/06.png)

En aquest cas farem a el disc.

![](img/07.png)

Triem el disc.

![](img/08.png)

Triem el lloc que volem que es copii.

![](img/09.png)

Li diem cada quan ha de fer la còpia (cada hora).

![](img/10.png)

Li diem que ho faci tots els dies.

![](img/11.png)

Que es guardi totes les còpies.

![](img/12.png)

I ja ho tindríem.
Ara farem el mateix però guardades en el drive.

![](img/13.png)
![](img/14.png)
![](img/15.png)
![](img/16.png)

Un cop triat farem el AuthID pel codi de autintificació.

![](img/17.png)

Aquest és el codi.

![](img/18.png)

Diem d'on es fa la còpia.

![](img/19.png)

Que es faci cada dia.

![](img/20.png)

I ja estaria.

![](img/21.png)

Ara crearem una carpeta i un document, que serviran per esborrar i tornar a restaurar. Fem una copia amb el fitxer còpiat

![](img/22.png)

Ho borrem

![](img/23.png)

I fem la restauració.

![](img/24.png)
![](img/25.png)
![](img/26.png)
![](img/27.png)
![](img/67.png)

Un cop feta mirem que tornem a veure el fitxer.

![](img/29.png)

I fem el mateix amb el drive.

![](img/30.png)
![](img/31.png)
![](img/32.png)
![](img/33.png)
![](img/34.png)
![](img/68.png)

## Copies Ubuntu
Primer creem el segon disc de 10 GB.

![](img/36.png)

Seguidament, creem la carpeta backup dins de media.

![](img/37.png)

Li donarem format al disc fent aquesta comanda i comprovem que estigui bé.

![](img/38.png)

Seguidament, crearem el volum del disc, per això primer haurem d'instal·lar el lvm2 i després fer-ho.

![](img/39.png)

Ara el tindrem que formatejar i montar el disc en la carpeta que hem creat al principi.

![](img/40.png)
![](img/41.png)

Seguidament, instal·lem el duplicity.

![](img/42.png)

Després crearem dos usuaris amb la seva carpeta personal.

![](img/43.png)

Crearem 4 arxius de 10 MB a la carpeta del meu usuari.

![](img/44.png)

Ara farem una copia de seguretat de home desde el root.

![](img/45.png)

I mirem que s’hagi copia la copia al disc (el dos).

![](img/46.png)

Ara borrem els arxius que haviem creat, per veure si ens surt bé la copia de seguretat.

![](img/47.png)
![](img/48.png)

Fem la restauració.

![](img/49.png)

I mirem que tornin a estar els arxius.

![](img/50.png)

Seguidament creem un nou arxiu de 4MB.

![](img/51.png)

Fem una copia.

![](img/52.png)

Ara per poder fer les còpies automàtiques primer tenim que desmuntar el disc.

![](img/53.png)

Crearem una script, pero primer crearem l’arxiu on estara l’escript.

![](img/54.png)
![](img/55.png)

I posem l’escript.

![](img/56.png)

Donem permisos al script.

![](img/57.png)
![](img/58.png)

Ara configurarem aquest arxiu per posar que es facin cada diumenge a les 23.

![](img/59.png)
![](img/60.png)

Ara fem el mateix que abans pero incremental.

![](img/61.png)
![](img/62.png)
![](img/63.png)
![](img/64.png)
![](img/65.png)
![](img/66.png)
