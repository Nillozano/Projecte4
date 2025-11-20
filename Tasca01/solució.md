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
