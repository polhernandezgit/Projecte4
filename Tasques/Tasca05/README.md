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
sudo nano /etc/ssh/ssh_config
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















