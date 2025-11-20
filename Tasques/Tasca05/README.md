# T05: Accés Remot. Connexió via SSH (tasca individual)
El primer que haurem de fer sera instal·lar el ssh.
``` bash
sudo apt install ssh
```
I mirem quina adreça té el server
``` bash
ip a
```

<img width="844" height="461" alt="image" src="https://github.com/user-attachments/assets/96aede1c-6068-4d5b-9f28-a333f5c0142f" />

<img width="817" height="336" alt="image" src="https://github.com/user-attachments/assets/34f5edeb-4b23-44ec-a39f-3d2a241d34bc" />

Ara connectarem la màquina de windows amb ssh i mirem si la connexiò està bé.
``` bash
ssh usuari@192.168.56.102
```
``` bash
hostname
```

<img width="711" height="512" alt="image" src="https://github.com/user-attachments/assets/daa258ff-c8b1-4d43-87cd-2c10e723cdc0" />

<img width="234" height="64" alt="image" src="https://github.com/user-attachments/assets/d0ca537e-e5d4-4d3f-850c-a02d2c6a81d4" />

Abans d'entrar a l'arxiu de configuració haurem d'habilitar l'usuari a root en el Ubuntu, que simplement es ficar la nova contrasenya que vulguem, en el meu cas usuari.
``` bash
sudo passwd root
```

<img width="301" height="67" alt="image" src="https://github.com/user-attachments/assets/8910316b-8520-4566-bd73-a0940e479ecb" />








