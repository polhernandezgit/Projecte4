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
Instal·larem el servidor NFS en la màquina Ubuntu i totes les dependencies.

<img width="636" height="221" alt="image" src="https://github.com/user-attachments/assets/acbe9ee8-dff9-4271-93e8-ae06abd1589e" />

### Fase 2: Preparació del servidor
Abans de compartir res, hem de preparar els usuaris i els directoris al Servidor.
1. Creació de Grups: Crear dos grups per al client: devs i admins.




