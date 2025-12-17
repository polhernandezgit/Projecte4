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
<img width="730" height="222" alt="image" src="https://github.com/user-attachments/assets/c1789c2b-5cd9-4fc8-93b3-57453f38b964" />

---
Ara podrem reiniciar i inicar el servei.
```
sudo systemctl restart nfs-kernel-server
```
```
sudo systemctl start nfs-kernel-server
```
<img width="469" height="16" alt="image" src="https://github.com/user-attachments/assets/257c6205-a144-4ed2-90a3-19cbcf84e0eb" />

<img width="729" height="143" alt="image" src="https://github.com/user-attachments/assets/adc81cd1-df8d-4831-98e1-1c7bea1f2bc7" />

---
Un cop fet això, hem de comprovar que funciona bé, per això hem de fer una comanda per veure quins fitxers podem exportar
```
sudo exportfs -u
```
<img width="272" height="34" alt="image" src="https://github.com/user-attachments/assets/ba418f0e-ca1c-4981-abee-3bcca00cfd8e" />

---
Utilitzarem la següent comanda per veure desde quin port treballa la ip de nomes anfitrió.
```
sudo rpcinfo -p 192.168.56.101
```
<img width="387" height="398" alt="image" src="https://github.com/user-attachments/assets/486efe02-f699-4617-9187-7e710b9c41ce" />

---
Ara el que farem sera connectar la màquina cient a la Ubuntu, per això instal·larem el següent paquet en la màquina Zorin.
```
sudo apt install nfs-common -y
```
<img width="644" height="375" alt="image" src="https://github.com/user-attachments/assets/968f31e8-c38a-4dff-a67d-3d1762c1c90c" />

---
I ara ens connectem.
```
sudo showmount -e 192.168.56.101
```
<img width="483" height="50" alt="image" src="https://github.com/user-attachments/assets/943be33e-8b8a-4956-b603-f699a9cbb0da" />

---
## Fase 3: L'Exportació d'Administració (El Dilema del root_squash)
El client necessita que el directori /srv/nfs/admin_tools sigui accessible per l'equip d'administradors. A vegades, l'usuari root del client (que sou vosaltres, els consultors) necessitarà escriure en aquest directori per instal·lar eines. Aquí mostrarem un error típic i la seva solució.

### Prova 1 (L'error comú)
### 1. Exportar el directori /srv/nfs/admin_tools amb les opcions 'rw,sync'.
Avans ja hem exportat el arxiu /srv/nfs en el arxiu de *exports*.
```
sudo nano /etc/exports
```

### 2. Des del client, muntar aquest recurs compartit a /mnt/admin_tools. Com a root del client, intentar crear un fitxer dins d'aquest directori muntat.
Primer crearem la carpeta

<img width="446" height="31" alt="image" src="https://github.com/user-attachments/assets/27bb89c9-797a-4c1b-8551-c7d03bedf153" />

---
Ara muntarem els recursos.

<img width="788" height="22" alt="image" src="https://github.com/user-attachments/assets/901df788-5212-44ae-9b58-46f5bec95b4d" />

---
Después d'això intentarem crear un arxiu a dins d'aqueta carpeta, per això anire als arixus de la màquina i entrarem a la carpteta *mnt*.

<img width="878" height="539" alt="image" src="https://github.com/user-attachments/assets/1c590917-447a-4570-9ddc-f3cc28e898c8" />

---
Ara entrarem a la carpeta creada ficant la contrasenya de la màquina.

<img width="881" height="540" alt="image" src="https://github.com/user-attachments/assets/9f448162-5780-4953-a5db-c5249dd15da4" />

---
I com podem veure no ens deixa veure el seu contingut

<img width="880" height="541" alt="image" src="https://github.com/user-attachments/assets/91f7b2d3-06ac-4d7d-b240-7d56ee977b41" />

### 3. Verificar quin és el propietari del fitxer creat. Per què? Justificar la resposta amb l'explicació tècnica de 'root_squash'.
El motiu per el que no ens deixa entrar a la carpeta es perquè no tenim permisos ni el *root_squash*, que el que passa és que el root de la màquina client no es el mateix que el de la màquina Ubuntu ( això ho solucionarem a l'activitat *Prova 2* ).

Avans el que farem és veure com el usuari Admin si ens deixa entrar en aqueslla carpeta. Primer iniciem sessió amb el usuari admin01.

<img width="608" height="395" alt="image" src="https://github.com/user-attachments/assets/ded2c303-59f7-44c8-ae6b-7c3ce6cb92ea" />

---
Intentem crear en la carpeta i podem vuere com si ens deixa, a més, fem un *ls* més la ruta de la carpeta per veure que s'ha creat.

<img width="465" height="53" alt="image" src="https://github.com/user-attachments/assets/f1848143-6d79-4022-9327-15f6ecea871e" />

---
### Prova 2 (La Solució)
### 1. Modificar l'exportació del directori /srv/nfs/admin_tools per incloure l'opció 'no_root_squash'.
Per començar hem de editar l'arxiu exports de la manera en que la línia que vam afegir fiquem *no_root_squash* més la segona línia i fem *restart* un cop guardat.

<img width="729" height="232" alt="image" src="https://github.com/user-attachments/assets/e52d43c3-4d94-4571-9d4c-5825e2d5070c" />

---
### 2. Al client, desmuntar i tornar a muntar el recurs compartit.
Primer desmuntem els recursos compartits.
```
sudo umount /mnt/admin_tools
```
<img width="454" height="30" alt="image" src="https://github.com/user-attachments/assets/2dbfd4ff-aaed-409e-b0f5-3624c21f22cb" />

---
Ara muntem la ip amb la ip de només anfitrió de la màquina Ubuntu.
```
sudo mount 192.168.56.101:/srv/nfs/admin_tools /mnt/admin_tools
```
<img width="640" height="105" alt="image" src="https://github.com/user-attachments/assets/d37c8ee1-775c-4a35-8213-eb2abaea148d" />

---
### 3. Com a root del client, intentar crear un fitxer dins d'aquest directori muntat. Observeu quin és el propietari del fitxer creat aquesta vegada. Ha canviat alguna cosa? Justificar la resposta amb l'explicació tècnica de 'no_root_squash'.

Ara crearem com a root el arxiu file02
```
touch /mnt/admin_tools/file02
```
<img width="533" height="29" alt="image" src="https://github.com/user-attachments/assets/f49ef646-06e3-4dbe-8eb5-262bfe4dca7b" />

---
Ara veiem com el propietari del arxiu file02 es root
```
ls -l /mnt/admin_tools
```
<img width="475" height="52" alt="image" src="https://github.com/user-attachments/assets/d4c965bd-2c3c-462d-bc1b-5c2a47483937" />

## Fase 4: L'Exportació de Desenvolupament (Permisos rw vs ro)
### 1. Editar /etc/exports per afegir dues exportacions per al mateix directori. El client vol que la xarxa d'administració (p.ex., 192.168.56.0/24) hi pugui escriure, però que la xarxa de consultors (simularem que és una altra IP, p.ex., 192.168.56.100) només pugui llegir.

Tornem a editar el arxiu exports borrant la segona línia i afegint les dos noves que surt en la imatge.
<img width="726" height="247" alt="image" src="https://github.com/user-attachments/assets/892fd958-334c-456b-94bd-ff9107fe1a8f" />

---
### 2. Des del client, muntar el recurs compartit a /mnt/dev_projects i provar d'escriure-hi com a usuari dev01. Hauria de funcionar.

Primer hem de muntar el recurs de dev_projects a la màquina client.
```
sudo mkdir /mnt/dev_projects
```
<img width="452" height="35" alt="image" src="https://github.com/user-attachments/assets/70ffa06d-238d-4083-a666-66fa64d82dff" />

---
Ara modificarem la xarxa des de *enp0s8* i probarem amb la següent ip.

<img width="641" height="399" alt="image" src="https://github.com/user-attachments/assets/370ae86e-699b-4982-981c-39aadfb2c67c" />

---
Ara muntem els recursos, primer farem la ip.
```
sudo mount 192.168.56.101:/srv/nfs/dev_projects /mnt/dev_projects
```
<img width="642" height="52" alt="image" src="https://github.com/user-attachments/assets/def9afdf-dfcd-4c4b-a18e-fa71c936d990" />

---
Iniciem sessió amb l'usuari dev01

<img width="594" height="392" alt="image" src="https://github.com/user-attachments/assets/be3db09c-70f8-40bd-bb36-c7b36d6762b2" />

---
Entrem a dins de la carpeta creada.
```
cd /mnt/dev_projects
```
<img width="377" height="35" alt="image" src="https://github.com/user-attachments/assets/a215edd5-f0de-4f05-a0d5-d883504f460d" />

---
Ara crearem el arxiu de prova en la carpeta i ls per comprovar que s'hagi creat.
```
touch file03
ls
```
<img width="441" height="50" alt="image" src="https://github.com/user-attachments/assets/6fb9784b-89ac-4145-8ae3-64ce258de746" />

### 3. Desmuntar el recurs i canviar manualment la IP del client a 192.168.56.100. Tornar a provar d'escriure al directori muntat com a usuari dev01 i comprovar que només funciona la lectura.
Tornem a entrar a la configuració de la xarxa i canviem la ip de manera que estigui a dins del rang que diu el enunciat.

<img width="642" height="399" alt="image" src="https://github.com/user-attachments/assets/d8049fb2-9b7b-4858-84d0-ec703f4c30d3" />

### 4. Canvieu d'usuari al client a admin01 i torneu a provar d'escriure al directori muntat. Comproveu que no es pot escriure, ja que admin01 no és membre del grup devs (permisos locals del sistema de fitxers).
Iniciem sessió amb admin01 per probar de crear un arxiu dins la carpeta i veure que no ens deixa.



