# T02: DPR: còpies de seguretat. Cas pràctic
## Part 1: Còpia seguretat dels equips clients Windows
Primer hem de instal·lar el windows 11 amb els dos discos de 10 GB.

<img width="1018" height="763" alt="image" src="https://github.com/user-attachments/assets/f2b479fa-18da-47a3-916e-c4749f9ac92c" />

---
Hem de tenir creats dos discos de minim 10 GB, un serà el que ja ve creat amb la màquina i l'altre el crearem nosaltres per fer les còpies de serguretat. 

<img width="865" height="493" alt="image" src="https://github.com/user-attachments/assets/9a889f04-3581-449e-83cd-6b53f767e40b" />

---
Quan haguem entrat a la màquina, el primer que hem de fer es anar al administrador de discos per crear un nou volum simple.

<img width="749" height="594" alt="image" src="https://github.com/user-attachments/assets/2287514c-d946-4d0c-9958-bafabed8e2f9" />

---
Haurem de anar al Google Drive per fer tota aquesta simulació.

<img width="1021" height="768" alt="image" src="https://github.com/user-attachments/assets/3f4b0244-b743-4dce-856d-9914dd9e79c6" />

---
Ara instal·laré el *Duplicati*.

<img width="1021" height="766" alt="image" src="https://github.com/user-attachments/assets/7a3a3edf-4e39-442b-9d74-4d11f82868e2" />

---
Crearem alguns documents temporals per fer les copies de seguretat.

<img width="778" height="584" alt="image" src="https://github.com/user-attachments/assets/192abf21-7264-4381-baa1-24294c74df06" />

---
I començarem a crears les còpies de seguretat.

<img width="1024" height="766" alt="image" src="https://github.com/user-attachments/assets/876e57c4-6efb-4218-a7bb-d8c79b01b8e4" />

<img width="1020" height="763" alt="image" src="https://github.com/user-attachments/assets/70303279-96e9-4c7c-8536-7a4c5e796a63" />

<img width="1014" height="766" alt="image" src="https://github.com/user-attachments/assets/5c2c8cc3-ec8e-485c-b526-9091412113d4" />

<img width="1015" height="692" alt="image" src="https://github.com/user-attachments/assets/9098b171-b984-479d-965a-9a0eb763fd27" />

---
Seleccionarem el disc secundari i la carpeta hon tenim els documents.

<img width="1013" height="688" alt="image" src="https://github.com/user-attachments/assets/636aba38-907d-4fde-aa33-2c4c548e68e3" />

<img width="949" height="683" alt="image" src="https://github.com/user-attachments/assets/04d0c086-e443-4abc-bfd2-834f13d4fc6b" />



---
Les copies de seguretat que aniran al disc secundari es repetiran cada hora.

<img width="1012" height="691" alt="image" src="https://github.com/user-attachments/assets/cd5d28dd-687e-4481-bc43-176c621f7487" />

---
En l'ultima pestanya nomès donem a *submit*.

<img width="1015" height="688" alt="image" src="https://github.com/user-attachments/assets/88124230-be32-4756-98ed-20b09a200277" />

---
Ara farem un backup que anirà al Google Drive, que en aquest cas hem de fer clic hon diu AuthID per vincular el nostre compte i que es farà cada dia a les 18:00 pm. La configuració sera igual que el backup anterior.

<img width="954" height="634" alt="image" src="https://github.com/user-attachments/assets/e928a566-c585-425c-b574-174ed1925570" />

<img width="960" height="583" alt="image" src="https://github.com/user-attachments/assets/21ef7be3-6253-4828-a701-bbae13554328" />

<img width="459" height="407" alt="image" src="https://github.com/user-attachments/assets/9229d9d9-491f-4269-a8aa-7732595158a4" />

---
Ara passarem a fer les restauracions. Per això hem de borrar els documents de prova que hem creat avans, per després anar a duplicati, donar a *restores* i *start*

<img width="780" height="588" alt="image" src="https://github.com/user-attachments/assets/5a71820e-1e62-448b-b273-da4845710494" />

<img width="1021" height="768" alt="image" src="https://github.com/user-attachments/assets/1a0feb5b-d2d7-4377-8cb6-7d100cf8086f" />

---
Aquì elegima la carpeta que volem recupera, en el meu cas és **Còpia de seguretat**.

<img width="947" height="634" alt="image" src="https://github.com/user-attachments/assets/36a0064a-a923-4ae0-bded-3fca8aba86bb" />

---
Escollim el fitxer que volem restaurar, que sera documents.

<img width="559" height="370" alt="image" src="https://github.com/user-attachments/assets/be52de9b-2f76-4f93-bd89-262672ecb4df" />

<img width="782" height="590" alt="image" src="https://github.com/user-attachments/assets/d7049a53-9527-457d-808b-e3f9d61f044c" />

I ja ho tindrem recuperat.
---
Per la còpia de seguretat del Google Drive el que haurem de fer serà exactament el mateix però nomes tindrem que elegir l'altre còpia.
## Part 2: Còpia seguretat servidor Linux
Primer hem de crear el disc secundari de 10 GB.

<img width="430" height="513" alt="image" src="https://github.com/user-attachments/assets/479e830e-4d21-455c-b96b-6793eda8eceb" />

---
Quan entrem a la màquina mirarem que el disc que hem creat està.

<img width="468" height="357" alt="image" src="https://github.com/user-attachments/assets/c17563e5-f824-4594-adbc-2154d89075bb" />

---
Ara hauremd de crear una partició en el disc. *n* per crear nova partició *p* és primaria *enter* per valor per defecte i *w* per guardar.
```
sudo fdisk /dev/sdb
```
<img width="641" height="335" alt="image" src="https://github.com/user-attachments/assets/cf4c45a7-46ba-419a-8f11-80f4f4feb03c" />

---
I mirem que s'ha creat correctament.

<img width="469" height="388" alt="image" src="https://github.com/user-attachments/assets/6ee801b6-d8cb-4faa-a739-5cf2dba792e5" />

---
Després li donarem format XFS.
```
sudo mkfs.xfs /dev/sdb1
```

<img width="625" height="176" alt="image" src="https://github.com/user-attachments/assets/f01aa074-6df4-42fa-96c4-ed219d78b140" />

---
Quan aguem formatat el disc, crearem el punt de muntatge manualment a */media/backup*, però primer creem la carpeta.
```
sudo mkdir -p /media/backup
```
```
sudo mount /dev/sdb1 /media/backup
```

<img width="418" height="51" alt="image" src="https://github.com/user-attachments/assets/10e2071f-ccd9-49e4-90da-c018be2b1f13" />

---
Ara passarem amb la instal·lació del Duplicity.
```
sudo apt install duplicity
```

<img width="854" height="223" alt="image" src="https://github.com/user-attachments/assets/57721768-6254-41ad-aae8-4bb390e1a58c" />

---
crearem uns usuaris amb carpeta personal.
```
sudo useradd -m -s /bin/bash user1
sudo useradd -m -s /bin/bash user2
```

<img width="412" height="45" alt="image" src="https://github.com/user-attachments/assets/008615e1-7857-402f-91c7-0ec497772bc5" />

---
I els i fiquem unes contrasenyes.
```
sudo passwd user1
sudo passwd user2
```

<img width="305" height="132" alt="image" src="https://github.com/user-attachments/assets/dc422408-36b3-455c-b373-6ea1f727493a" />

---
Crearem 4 arxius de 10 MB a la carpeta home de l'usuari principal.
```
fallocate -l 10MB arxiu1
fallocate -l 10MB arxiu2
fallocate -l 10MB arxiu3
fallocate -l 10MB arxiu4
```

<img width="331" height="102" alt="image" src="https://github.com/user-attachments/assets/db443b28-0648-45f6-8004-dc495d5dd805" />

---
Ara fem la copia de seguretat de la carpeta home
```
sudo duplicity full /home/ file:///media/backup/
```

<img width="404" height="282" alt="image" src="https://github.com/user-attachments/assets/23003d67-19e0-491f-a450-ad377f0f73cb" />

---
I mirem com s'han creats els arxius.

<img width="489" height="61" alt="image" src="https://github.com/user-attachments/assets/a27cd03e-85d0-4c5a-8c04-9162407b4de4" />

---
Després de tot això, borrarem els fitxers de prova i farem la restauració.
```
rm arxiu1
```
```
sudo duplicity restore file:///media/backup/ /home/usuari
```

<img width="259" height="65" alt="image" src="https://github.com/user-attachments/assets/43f5d6cf-2463-433c-a6ac-bdadb5ef626d" />

<img width="692" height="62" alt="image" src="https://github.com/user-attachments/assets/130247a0-c5bc-4b29-9c51-a0561eea9d0e" />

<img width="252" height="100" alt="image" src="https://github.com/user-attachments/assets/13f08e13-9576-4d99-9d88-f031e2426433" />

---
Ara per fer la copia incremental, primer hem de crear un altre arxiu de 4 MB.

<img width="383" height="47" alt="image" src="https://github.com/user-attachments/assets/9547ce98-9452-479a-9c20-45c76e1492fc" />

---
Fem una nova còpia que detecta només un fitxer nou i fa una còpia incremental.

<img width="836" height="382" alt="image" src="https://github.com/user-attachments/assets/ebb88953-ae63-4015-8914-1512f477eb43" />

---
Ara passarem a fer els scripts per fer còpies automàtiques.
Primer desmuntem la unitat del bakcup.
```
sudo umount /media/backup
```
I editem el fitxer *Fullbackup.sh*.

<img width="431" height="113" alt="image" src="https://github.com/user-attachments/assets/2544d4a4-8dc4-40c9-9b13-714eca6967ae" />

---
Després donem permisos d'execució














