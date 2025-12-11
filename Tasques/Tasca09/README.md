# T09: Servidor fitxers Linux. NFS (tasca individual)
## El Cas Client: DevOptimize Solutions
El nostre client, DevOptimize Solutions, és una petita startup de desenvolupament de programari que treballa exclusivament amb Linux. Tenen un problema crític: el seu codi font i els seus actius (documents de disseny, scripts) estan descontrolats. Cada desenvolupador té còpies locals, cosa que provoca errors de versió constants i una pèrdua d'eficiència brutal. Ens han contractat per implementar un servidor de fitxers centralitzat. Atès que tot l'entorn és Linux, la solució nativa, més ràpida i eficient del sector és NFS (Network File System). El client ha insistit en que treballa sense un entorn d’autenticació centralitzada i que, de moment, no té previst fer aquest pas.

Per mostrar al client com quedarà la solució proposada a partir de les seves demandes i poder mostrar també les seves limitacions, se t’encarrega fer una demostració del sistema.

Crearàs un servidor NFS (NFSv3) i un client Linux que consumeixi els recursos compartits. Hauràs de crear usuaris i grups per simular l'entorn del client i demostrar el control d'accés utilitzant les opcions d'exportació (/etc/exports) i els permisos del sistema de fitxers (chmod, chown).

## Fases del projecte
### Fase 1: Preparació de l'entorn
Per preparar aquesta prova de concepte, necessitaràs dues màquines virtuals Linux: tot i que pel servidor podríem fer servir qualsevol distribució, ens decantarem per Ubuntu Server 24.04 LTS per la seva facilitat d'ús i popularitat. Per al client, utilitzarem Zorin OS 18. Els dos equips els configurarem amb dues interfícies de xarxa: una NAT per a l'accés a Internet i una adaptador de xarxa només-amb-amfitrió per a la comunicació entre ells i potencialment, treballar via terminal SSH amb el servidor.

Tots dos equips els instal·larem seguint els requisits recomanats. L'idioma triat serà espanyol (Espanya) i amb l'idioma per defecte en espanyol. En el cas d'Ubuntu Server, seleccionarem la instal·lació del servei SSH durant el procés d'instal·lació per facilitar la gestió remota.

Ens assegurarem que ambdues màquines tinguin accés a Internet i que es puguin comunicar entre elles a través de la xarxa només-amb-amfitrió i actualitzarem els sistemes amb les últimes actualitzacions disponibles.

<img width="599" height="289" alt="image" src="https://github.com/user-attachments/assets/f5fcad56-609b-49d8-8e37-5adfc3ef38a8" />

<img width="600" height="298" alt="image" src="https://github.com/user-attachments/assets/2b0cb223-1a56-44f9-a5c6-9ac2c625fb07" />

---
Ficarem aquestes interficies en les dos màquines virtuals.

<img width="864" height="494" alt="image" src="https://github.com/user-attachments/assets/cb6a41fd-a4dd-400a-8000-04eadbb892a5" />

<img width="863" height="495" alt="image" src="https://github.com/user-attachments/assets/9ac7bd20-9b82-4301-99e8-d9125215d84f" />

---
Comprobarem si les màquines es poden comunicar.

<img width="496" height="130" alt="image" src="https://github.com/user-attachments/assets/5fb08a9a-837c-4516-b78b-2623099bc0ac" />

---
Actualitzarem la màquina.
```
sudo apt upgrade
```
```
sudo apt update
```

<img width="657" height="257" alt="image" src="https://github.com/user-attachments/assets/7e079e0e-e216-436c-9e5b-88fb3d77f44f" />

<img width="667" height="239" alt="image" src="https://github.com/user-attachments/assets/534107d6-2319-43ac-8f6a-91674886d8bc" />

### Fase 2: Preparació del servidor
Abans de compartir res, hem de preparar els usuaris i els directoris al Servidor.
### 1. Creació de Grups: Crear dos grups per al client: devs i admins.
```
sudo groupadd devs
```
```
sudo groupadd admins
```
<img width="300" height="32" alt="image" src="https://github.com/user-attachments/assets/832e856f-d157-4103-8daf-fd02d629801a" />

---
### 2. Creació d'Usuaris: Crear un usuari dev01 (membre del grup devs).
```
sudo useradd -m /bin/bash -G devs dev01
```
<img width="473" height="27" alt="image" src="https://github.com/user-attachments/assets/dc3520e4-49d0-4e7b-a057-1912a246ed29" />

---
### 3. Crear un usuari admin01 (membre del grup admins). Creació de Directoris (al Servidor):
```
sudo useradd -m -s /bin/bash -G admins admin01
```
<img width="510" height="26" alt="image" src="https://github.com/user-attachments/assets/7e3fa53b-a42e-44a9-bc6e-3d77ab9d4629" />

---
### 4. Crear el directori per als projectes de desenvolupament: /srv/nfs/dev_projects
```
sudo mkdir -pv /srv/nfs/dev_projects
```
<img width="429" height="46" alt="image" src="https://github.com/user-attachments/assets/e8793a8d-ba9d-45d0-87db-05941dc8ea0b" />

---
### 5. Crear el directori per a les eines d'administració: /srv/nfs/admin_tools
```
sudo mkdir -pv /srv/nfs/admin_tools 
```
<img width="420" height="29" alt="image" src="https://github.com/user-attachments/assets/2447b02f-2b33-456b-bb28-e55ba563df85" />

---
### 6. Permisos del Servidor (El punt clau):
- Es vol que els developers tinguin control total sobre els seus projectes.
- Es vol que els administradors tinguin control sobre les seves eines.
```
sudo chown :devs dev_projects/
```
```
sudo chown :admins admin_tools/
```
<img width="450" height="94" alt="image" src="https://github.com/user-attachments/assets/be1f2482-bf69-434a-ae82-4c2919f2e904" />

Permisos del Servidor (El punt clau):

- Es vol que els developers tinguin control total sobre els seus projectes.
- Es vol que els administradors tinguin control sobre les seves eines.
- En tots dos casos, l'usuari propietari serà root.
```
sudo chmod 770 admin_tools/ dev_projects/
```
<img width="526" height="80" alt="image" src="https://github.com/user-attachments/assets/c3105a61-236c-47da-aaac-7f575f8b405b" />

### Farem el mateix en la màquina Zorin
Primer haurem d'instal·lar l'aplicació de *users and groups*.
<img width="897" height="556" alt="image" src="https://github.com/user-attachments/assets/3f12742e-cdf9-4a50-87cb-f713aaf00e62" />

---
Quan obrim l'aplicació veurem que nomes tenim el nostre usuari, però per poder crear els usuaris i grups, hem de fer clic a gestionar grupos.
<img width="740" height="427" alt="image" src="https://github.com/user-attachments/assets/6f2ae980-8bed-4031-b995-b5ed63aac06e" />

---
Quan donem a gestionar grupos, cliquem a Añadir.
<img width="735" height="423" alt="image" src="https://github.com/user-attachments/assets/97033f4d-24ef-4e78-ab79-8bf9874a9418" />

---
Aqui fiquem el primer grup de *devs*.
<img width="732" height="427" alt="image" src="https://github.com/user-attachments/assets/8ce5a45d-9f14-433f-802e-700415d78b72" />

---
I el segon sera *admins*.
<img width="734" height="428" alt="image" src="https://github.com/user-attachments/assets/6518fc6a-d07a-43d9-9ede-21780b9f7fab" />

---
Un cop creats el grups, ara crearem els usuaris, per això tornem al menú principal i donem a *Añadir*
<img width="735" height="430" alt="image" src="https://github.com/user-attachments/assets/efe68a8d-f03e-4a3e-ab64-6a6e7b8be03a" />

---
Crearem el primer usuari, que serà *dev01*.

<img width="291" height="570" alt="image" src="https://github.com/user-attachments/assets/a77bdf52-04fc-4819-b97d-131c61f828e3" />

---
I li ficarem una contrasenya.

<img width="522" height="396" alt="image" src="https://github.com/user-attachments/assets/1c7582a1-d9ee-4047-982e-03d0b6ba96e0" />

---
Farem el mateix amb l'usuari *admin01*

<img width="292" height="571" alt="image" src="https://github.com/user-attachments/assets/61ebf93e-5939-4e5e-a6fc-b7508b7c90e6" />

---
Ara hem d'afegir els usuaris als grups corresponents, per això hem de entrar a la pestanya de *gestionar grupos*, seleccionar els usuaris, entrar a *propiedades* i configurar-los com en les imatges.

<img width="327" height="292" alt="image" src="https://github.com/user-attachments/assets/da130d39-a9eb-4224-8be3-fcb72020f04a" />

<img width="328" height="293" alt="image" src="https://github.com/user-attachments/assets/fa73a85a-5347-4582-b7d3-bf27043aa8b7" />

### 7. Com a pas final, s'instal·laran els paquets necessaris per al servei NFS al servidor i es configurarà l'exportació dels directoris amb les opcions adequades.
```
sudo apt install nfs-kernel-server
```

<img width="636" height="221" alt="image" src="https://github.com/user-attachments/assets/acbe9ee8-dff9-4271-93e8-ae06abd1589e" />

---
Ara hem de fer les exportacions dels directoris amb les opcions correctes, que per això hem d'editar l'arxiu */etc/exports* i afegir la següent línia.
```
sudo nano /etc/exports
```
```
/srv/nfs 192.168.56.105(rw,sync)
```
<img width="729" height="197" alt="image" src="https://github.com/user-attachments/assets/92cf78d1-f62e-4beb-9bf6-e3dfafec23c2" />

---
Ara podrem inicar el servei.
```
sudo systemctl start nfs-kernel-server
```
<img width="729" height="143" alt="image" src="https://github.com/user-attachments/assets/adc81cd1-df8d-4831-98e1-1c7bea1f2bc7" />

---
Ara instal·larem el servei en la màquina Zorin.
```
sudo apt install nfs-common -y
```
<img width="644" height="375" alt="image" src="https://github.com/user-attachments/assets/968f31e8-c38a-4dff-a67d-3d1762c1c90c" />

---



