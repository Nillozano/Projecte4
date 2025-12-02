# T01: DRP: còpies de seguretat. Estudi cas client (treball cooperatiu)
## FASE 1:
###  1.Què copiar? (Priorització): Quines són les dades més crítiques del servidor? Cal fer còpia dels 10 equips clients? Justifica-ho.
Les dades més crítiques del servidor són:

Bases de Dades (Comptabilitat i Clients): Crítiques i d'ús diari.

Documents de Projectes: Plànols i especificacions tècniques.

Carpetes Personals dels Usuaris: Importants però menys crítiques.



- No és estrictament necessari fer còpia completa, ja que la majoria de dades són al servidor.
- Recomanable fer còpia de la carpeta Documents dels tècnics.



### 2. Periodicitat i Tipus de Còpia: Proposa un calendari bàsic per a la setmana (Diari/Setmanal/Mensual) i quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) per a les dades crítiques.

**Bases de Dades (Comptabilitat/Clients):**

Diària: Còpia incremental cada 4 hores.

Setmanal: Còpia completa cada diumenge.

**Documents de Projectes i Carpetes Personals:**

Diària: Còpia incremental.

Setmanal: Còpia diferencial.

Mensual: Còpia completa.

**Tipus de còpia:**

Completa: Setmanal i mensual.

Incremental: Diària.

Diferencial: Setmanal.



### 3. Mitjans i Ubicació: Quin tipus de mitjà de còpia utilitzaries (Discs durs externs, NAS, Cloud, Cintes)? On s'hauria de guardar físicament la còpia més recent (Regla 3-2-1).
**Mitjans:**

NAS intern per còpies ràpides.

Cloud per còpia externa segura.

Discs durs externs per còpia mensual.

**Ubicació segons la regla 3-2-1:**

3 còpies: Original + NAS + Cloud.

2 tipus de mitjans: NAS i Cloud.

1 còpia fora de l’empresa: Al núvol.

La còpia més recent hauria d’estar al NAS intern per restauració ràpida.

---
## FASE 2:

### **Esquema 3-2-1 de Còpies**

| **Element**             | **Proposta de la Parella**                                                                                                                                                                                      | **Justificació**                                                                                                                                    |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Dades Crítiques**     | - Bases de Dades (Comptabilitat i Clients): Crítiques i d’ús diari.<br>- Documents de Projectes: Plànols, especificacions tècniques.<br>- Carpetes Personals dels Usuaris: Són mportants per la feina. | Les Bases de Dades són super importants per la feina diària, els projectes són essencials per als serveis i les carpetes personals contenen informació de treball i això també és molt important. |
| **Periodicitat (BD)**   | - Cada 4 hores: còpia incremental de les Bases de Dades.<br>- Diària: còpia incremental del servidor.<br>- Setmanal: còpia completa.<br>- Mensual: còpia completa per conservar un historial.                       | Complir l’objectiu de pèrdua màxima de dades (RPO), que vol dir que les Bases de Dades no poden perdre més de 4 hores de feina. A més, assegurem la protecció general fent còpies freqüents i còpies completes cada cert temps.                                                             |
| **Tipus de Còpia (BD)** | - Incremental: cada 4 hores per Bases de Dades i diària per altres dades.<br>- Diferencial: setmanal per projectes i carpetes.<br>- Completa: mensual per tot el servidor.                                      | Les còpies incrementals estalvien espai i temps, les còpies diferencials faciliten la restauració i les còpies completes garanteixen que es conserva tota la informació.                                             |
| **Mitjà 1 (Local)**     | NAS intern per còpies diàries i setmanals.                                                                                                                                                                  | Restauració ràpida dins l’empresa, assegurant que es pot recuperar tot en menys de 4 hores.                                                                                               |
| **Mitjà 2 (Extern)**    | Núvol per còpia fora de l’empresa + Disc dur extern per còpia mensual.                                                                                                                                  | El núvol protegeix davant desastres físics (com incendis o robatoris) i el disc dur extern és una còpia addicional que es pot guardar fora de l’empresa.                                                                   |

---

### **Regla 3-2-1 aplicada**

  3 còpies: Original + NAS + Núvol/Disc dur
  2 mitjans diferents: NAS i Cloud
  1 fora de l’empresa: Núvol

---
## FASE 3:

## 1. Debat i selecció
Cada parella presenta el seu esquema.  
El grup debat els pros i contres (cost, temps de recuperació, seguretat, simplicitat).

## 2. Disseny de la política final
El grup redacta la política definitiva de còpies de seguretat per a l’empresa.

---

# Document final

## 1) Dades objecte de còpia

Les dades més importants del servidor són sobretot les **bases de dades dels clients**, perquè són importants per al funcionament de l’empresa i canvien contínuament. També són molt importants els **documents de projectes**, ja que inclouen plànols i especificacions necessàries per a la feina dels tècnics. Finalment, les **carpetes personals dels usuaris** també s’han de protegir, perquè contenen informació del treball diari. No cal fer còpia completa dels 10 equips clients, ja que gairebé tot el treball es guarda en un NAS.

Les **bases de dades** s’han de copiar amb còpies incrementals cada 4 hores i una còpia completa setmanal, ja que són dades crítiques. Els **documents de projectes** tindran còpia diferencial diària i còpia completa setmanal. Les **carpetes personals** es copiaran cada nit amb còpies incrementals i una còpia completa setmanal.

---

## 2) Cronograma setmanal

| Dia | Dades | Tipus de còpia | Mitjà |
|-----|--------|----------------|------|
| Dilluns | Base de dades | Incremental | NAS |
| Dimarts | Base de dades | Incremental | NAS |
| Dimecres | Base de dades | Incremental | NAS |
| Dijous | Base de dades | Incremental | NAS |
| Divendres | Base de dades | Incremental | NAS |
| Dissabte | Documents projecte | Diferencial | NAS |
| Diumenge | Tot el servidor | Completa | NAS + Cloud |

---

## 3) Elecció de mitjans i ubicació (Regla 3-2-1)

### Mitjà 1 (Local)
El mitjà de còpia local serà un NAS instal·lat a l’empresa. Servirà per fer còpies freqüents del servidor i permet una recuperació ràpida de les dades en cas d’error

### Mitjà 2 (Extern)
La còpia externa es farà al núvol (cloud) utilitzant un proveïdor de confiança com Google Cloud o Microsoft Azure.

### Ubicació fora de lloc
La còpia externa es guarda al núvol, en un lloc fora de l’empresa, perquè així les dades estan protegides encara que passi alguna cosa greu a les oficines, com un incendi o un robatori.

---

## 4) Estratègia de recuperació (RTO/RPO)

Per assegurar que no es perden més de 4 hores d’informació de comptabilitat i clients, es fan còpies de seguretat cada 4 hores. Així, si hi ha algun problema, la informació recuperada sempre serà recent. També per garantir que les dades es puguin recuperar en menys de 4 hores, la còpia més recent es guarda al NAS de l’empresa, que permet restaurar les dades ràpidament sense necessitat d’esperar descàrregues del núvol.
