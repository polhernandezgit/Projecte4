# T06: Accés remot. Escriptori remot (RDP) (tasca individual)
## Configuració interficies
Primer hem de posar la màquina windows i la zorin en *xarxa NAT* perquè es puguin veure i tinguin connexio a internet

<img width="863" height="492" alt="image" src="https://github.com/user-attachments/assets/1a89eaa4-4999-43ea-92ce-176003f6d283" />

<img width="860" height="493" alt="image" src="https://github.com/user-attachments/assets/aea96d78-6460-4491-90bf-1a7506c29fdd" />

## Configuració màquina Windows.
Quan entrem a la màquina windows hem de anar a configuració i en la pestanya de acces remot hem de activarla per que la altre màquina pugui connectarse

<img width="793" height="624" alt="image" src="https://github.com/user-attachments/assets/83d2539b-2250-438f-8b66-d32df7b5630e" />

---
Ara entrem a *Usuarios de Escrtorio remoto* per dir quins usuaris tindran el permis de connectarse remotament.

<img width="796" height="625" alt="image" src="https://github.com/user-attachments/assets/4cc0767f-2695-4f4d-9cd3-980f426c6382" />

---
En la pestanya que ens sortirà, cliquem en *agregar*.

<img width="374" height="328" alt="image" src="https://github.com/user-attachments/assets/e9e76ec4-7a20-4a99-8eb1-cc67d5d8981b" />

---
I posem el que surt en pantalla. Hem de ficar el mateix usuari que surt en la part de *desde esta ubicacion* més *usuari*.

<img width="466" height="328" alt="image" src="https://github.com/user-attachments/assets/9388262e-7d76-439a-a433-907754da8fae" />

---
Com podem veure, ja ens surt el usuari.

<img width="370" height="327" alt="image" src="https://github.com/user-attachments/assets/0d0d838c-aa11-42c8-957c-718dc642272f" />

---
També hem de desactivar el firewall.

<img width="793" height="628" alt="image" src="https://github.com/user-attachments/assets/0565f359-db2d-4e51-8d35-c2ce0a0a5690" />

## Configuració màquina Zorin
En la màquina zorin també anirem a la configuració, sistema i a acces remot.

<img width="807" height="630" alt="image" src="https://github.com/user-attachments/assets/fd87c3c8-f8f7-4c88-b0c1-8edee06a7aef" />

---
Aqui hem de activar les primeres dos opcions i podrem veure que ens surt el usuari i el port.

<img width="678" height="627" alt="image" src="https://github.com/user-attachments/assets/d031a752-4a15-4371-a675-999efa112c78" />

## Conexió desde Zorin a Windows
Per poder connectarnos anem al powershell de windows i farem *ipconfig* per veure la ip.

<img width="623" height="252" alt="image" src="https://github.com/user-attachments/assets/9691fd18-61f2-4f1a-89f4-1d48016e5f45" />

---
I per connectarnos desde Zorin, buscarem Remmina i entrarem.

<img width="503" height="568" alt="image" src="https://github.com/user-attachments/assets/42a32f7c-a14a-40ca-9e36-b49f2b9fad7c" />

---
I a la part de adal posarem la ip de Windows.

<img width="645" height="436" alt="image" src="https://github.com/user-attachments/assets/612822f9-408a-45b5-8608-62fcb3cf88fd" />

---
Ens sortirà aquesta pestanya i només donem a *sí*.

---
Després aqui fiquem algunes dades de la màquina windows.

<img width="796" height="507" alt="image" src="https://github.com/user-attachments/assets/734c5f9f-b4a8-475c-9824-c9eb5712cfee" />

---
I ja estarem connectats.

<img width="662" height="506" alt="image" src="https://github.com/user-attachments/assets/db90348d-bb64-4423-b301-acb099693fdd" />

## Connexió desde Windows a Zorin.
Desde la màquina Zorin, entrarem al terminal i fem *ip a* per veure la ip.

<img width="644" height="266" alt="image" src="https://github.com/user-attachments/assets/721f6e9f-5d92-4d11-9f49-92ea089014ce" />

---
Ara entrarem a l'aplicació de *Conexión i Escritorio remoto* i a dins, ficarem la ip de la màquina Zorin i donem a *conectar*.

<img width="400" height="240" alt="image" src="https://github.com/user-attachments/assets/7106b812-759e-40d5-8b3d-39d480e6678f" />

---
Ara ens demanarà el nom d'usuari i la contrasenya, però no es de la màquina. Per veure quines són anem a la configuració de màquina Zorin, sistema, escritoris remots i posarem les credencials de abaix.

<img width="953" height="635" alt="image" src="https://github.com/user-attachments/assets/e5f90b08-6abb-4878-9e8a-290499c93244" />

<img width="957" height="634" alt="image" src="https://github.com/user-attachments/assets/6fce4ede-d2b5-4acf-ac5e-85814fa1f3c4" />

<img width="452" height="371" alt="image" src="https://github.com/user-attachments/assets/40deaa42-7d47-4f57-b9a2-ca88b56a2bec" />

---
Ens sortira aquesta sertificació, nomes donem a sí.

<img width="383" height="396" alt="image" src="https://github.com/user-attachments/assets/ad8be3ce-e71f-4d79-8704-20f2b4f98676" />

---
I ja podem veure i controlar la màquina Zorin

<img width="959" height="749" alt="image" src="https://github.com/user-attachments/assets/e516c4a4-a1e4-4faf-a2d2-413e4b0892cf" />

