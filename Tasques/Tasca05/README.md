# T05: Accés Remot. Connexió via SSH (tasca individual)
El primer que haurem de fer sera instal·lar el **ssh**.
``` bash
sudo apt install ssh
```
I mirem quina adreça té el server
``` bash
ip a
```

<img width="844" height="461" alt="image" src="https://github.com/user-attachments/assets/96aede1c-6068-4d5b-9f28-a333f5c0142f" />

<img width="817" height="336" alt="image" src="https://github.com/user-attachments/assets/34f5edeb-4b23-44ec-a39f-3d2a241d34bc" />

---

Ara connectarem la màquina de **windows amb ssh** i mirem si la connexiò està bé.
``` bash
ssh usuari@192.168.56.102
```
``` bash
hostname
```

<img width="711" height="512" alt="image" src="https://github.com/user-attachments/assets/daa258ff-c8b1-4d43-87cd-2c10e723cdc0" />


<img width="234" height="64" alt="image" src="https://github.com/user-attachments/assets/d0ca537e-e5d4-4d3f-850c-a02d2c6a81d4" />

---

Abans d'entrar a l'arxiu de configuració **haurem d'habilitar l'usuari a root en el Ubuntu**, que simplement es ficar la **nova contrasenya que vulguem**, en el meu cas *usuari*.
``` bash
sudo passwd root
```

<img width="301" height="67" alt="image" src="https://github.com/user-attachments/assets/8910316b-8520-4566-bd73-a0940e479ecb" />

---

Ara entrarem a **l'arxiu de configuració**, que es troba a:
``` bash
sudo nano /etc/ssh/sshd_config
```
I al final de l'arxiu afegirem la linea hon diu *AllowUsers usuari*.

<img width="555" height="723" alt="image" src="https://github.com/user-attachments/assets/a08c9a74-7f99-41ac-93e2-afb25f527254" />

---

Després farem un *login* en local amb **l'usuari root**.
``` bash
su - root
```

<img width="219" height="47" alt="image" src="https://github.com/user-attachments/assets/2c34bd3f-4b24-4d43-a5d3-3d4c761607fb" />


<img width="210" height="77" alt="image" src="https://github.com/user-attachments/assets/95c3f420-45c4-4c35-8d96-e85eb8133497" />

---

Ara tornem a la màquina windows per intentar fer un *ssh root* i veurem que ens denega la contrasenya.

<img width="436" height="77" alt="image" src="https://github.com/user-attachments/assets/4e8ad437-0d89-434d-a912-47e919b45c4d" />

---

Aqui haurem de generar alguns codis *RSA*. Nomes hem de donar enter fins que es completin.

<img width="665" height="398" alt="image" src="https://github.com/user-attachments/assets/1beb2d31-107c-4107-a14f-b5c45d35899a" />

---

Despres mirarem si tenim els **arxius que necessitem** ( aixo nomes m'ha funcionat amb terminal ).

<img width="609" height="247" alt="image" src="https://github.com/user-attachments/assets/5b141d02-c413-4ffc-889a-58cdf0d79357" />

---

I a continuació hem de copiar el .pub de la VM Ubuntu i copiarla al windows amb la següent comanda:
``` bash
scp .\.ssh\id_rsa.pub usuari@192.168.56.102:/home/usuari
```

<img width="951" height="79" alt="image" src="https://github.com/user-attachments/assets/67915f9d-8ea4-42c4-a0b8-05d4e8574040" />

<img width="602" height="289" alt="image" src="https://github.com/user-attachments/assets/8c99c953-8657-4228-bfdb-71faad69b556" />

---

Tornarem a la màquina Ubuntu per crear el següent arxiu a dins de la carpeta ssh amb aquesta comanda.
``` bash
touch .ssh/authorized_keys
```

<img width="346" height="30" alt="image" src="https://github.com/user-attachments/assets/23e922f4-e0ef-4898-80f6-eb5cf49bad8a" />

---

Ara copiem la clau id_rsa.pub dins de l'arxiu que acabem de crear:
``` bash
cat id_rsa.pub >> .ssh/authorized_keys
```

<img width="444" height="30" alt="image" src="https://github.com/user-attachments/assets/2c27aea4-5775-422d-b54b-dd35f5be4b03" />

---

Tornem a la màquina windows per fer un ssh a la nostre ip per veure si ara ens demana la nostra contrasenya.

<img width="713" height="549" alt="image" src="https://github.com/user-attachments/assets/5541082a-c774-49a0-9f0d-111112e778f7" />

---

Després anem a la configuració de sistema i a caracteristiques opcionals per permitir que l'aplicació fagi canvis en el dispositiu.

<img width="1017" height="735" alt="image" src="https://github.com/user-attachments/assets/6db1883e-1ead-4a92-9d8a-b0e0cb6462fe" />

<img width="460" height="412" alt="image" src="https://github.com/user-attachments/assets/a9e840f1-7ed2-4546-ae1e-07dd4b00fcbc" />

<img width="453" height="375" alt="image" src="https://github.com/user-attachments/assets/1ab377b2-1158-419f-890d-5295fb05ff47" />

---

Un cop a qui dins donem a ver las caracteristiques disponibles.

<img width="541" height="623" alt="image" src="https://github.com/user-attachments/assets/27b700f9-533b-4f5f-9d56-8afb19baa92f" />

---

Buscarem el OpenSSH, marquem la casella i afegir.

<img width="540" height="623" alt="image" src="https://github.com/user-attachments/assets/b142c7f8-c91c-46a5-a088-ef03a4c1e09e" />

---

En el següent pas, haurem d'apagar el firewall en el windows buscant firewall y proteccion de red.
Després entrem a red pública i la desactivem.

<img width="793" height="629" alt="image" src="https://github.com/user-attachments/assets/8a715496-b06c-4813-a33c-1ac6023d0642" />

<img width="549" height="627" alt="image" src="https://github.com/user-attachments/assets/d5256445-13b3-4a40-bb09-96ef7e79448c" />

---

Ara tornem a entrar al pwershell pero aquest cop com a administradors i activem el ssh.

``` bash
Start-Service sshd
```

<img width="400" height="221" alt="image" src="https://github.com/user-attachments/assets/14bbebba-b49a-4951-9e29-bd660380a72a" />

<img width="392" height="125" alt="image" src="https://github.com/user-attachments/assets/15ce5f04-971b-4ef9-b644-a6e2010da53c" />

---

I fem que cada cop que iniciem la màquina, tambe s'encéngui el servei.

``` bash
Set-Service -Name sshd -StartupType "Automatic"
```

<img width="576" height="31" alt="image" src="https://github.com/user-attachments/assets/6825428f-cb35-4799-8310-3de64bb56ddd" />

---

Després farem un ipconfig per veurela ip que te la interficie de hostonly, que la utilitzarem per conectar-nos en la màquina Ubuntu

``` bash
ipconfig
```

<img width="610" height="369" alt="image" src="https://github.com/user-attachments/assets/8f73b5b9-4abf-47c2-a869-17c6b286bd2d" />

---

Començarem connectan-nos remotament amb la màquina Ubuntu a la màquina windows de la següent manera:
Primer farem un ping amb la ip de hostonly de la màquina windows per veure si les dos màquines es poden comunicar.

<img width="505" height="97" alt="image" src="https://github.com/user-attachments/assets/1bcf8e05-de94-4683-9573-2794761dbeaa" />

---

Com que la comprovació ens confirma que funciona bé, ens connectem a la màquina windows

``` bash
ssh usuari@192.168.56.103
```

<img width="340" height="35" alt="image" src="https://github.com/user-attachments/assets/17a0bb66-7c19-4d55-88e1-d55078eec7b8" />

## Creació d'un túnel.
Tornarem al powershell de windows per començar a crear el túnel.

``` bash
ssh -D 9876 usuari@192.168.56.102
```

<img width="624" height="531" alt="image" src="https://github.com/user-attachments/assets/abaf126a-924e-4b14-a96c-37cb1ff24ddb" />

---

Ara configurarem el túnel amb proxy.
Hem de anar a panel de control, Redes e internet i a opciones de internet.

<img width="778" height="582" alt="image" src="https://github.com/user-attachments/assets/378216a4-c911-4437-ba09-c9b5503283b4" />

<img width="780" height="345" alt="image" src="https://github.com/user-attachments/assets/42ad18b2-8717-4ae9-ac8c-cf14ee2b8977" />

---

En aquesta part hem de anar a conexiones, que surt en la part de adalt i donem a configuración de LAN, activem el servidor proxy, donem a opciones avanzadas i ho configurem.

<img width="415" height="569" alt="image" src="https://github.com/user-attachments/assets/573b2084-45d1-4484-bbf2-dfe7f7db7005" />

<img width="427" height="576" alt="image" src="https://github.com/user-attachments/assets/62ef9fa6-3a4c-4d5c-bad5-5a650037de2e" />

<img width="425" height="576" alt="image" src="https://github.com/user-attachments/assets/512270db-d721-45b6-9906-d20f9cc19b3c" />

---



