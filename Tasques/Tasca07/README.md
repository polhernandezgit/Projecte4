# T07: Accés remot. Serveis d’assistència remota
Molt bé, equip. Fins ara hem vist eines per administrar servidors (SSH, RDP, VNC). Però la realitat de la nostra feina a EverPia és que una gran part de les nostres hores facturables provenen del suport directe a l'usuari final (Helpdesk).

Quan un client truca perquè "el PDF no s'obre", "li ha desaparegut una icona" o "la impressora no imprimeix", no li podem demanar que configuri una VPN o obri el port 3389 del seu router. Necessitem una eina d'assistència remota sota demanda: ràpida, fiable, segura i que funcioni en segons, fins i tot en xarxes restrictives.

La direcció d'EverPia ha decidit estandarditzar l'eina oficial que farem servir per a aquestes tasques de suport immediat. La vostra missió en parelles és analitzar el mercat i proposar la millor solució, per després crear la documentació que faran servir tant els nostres tècnics com els nostres clients.
## Fase 1: Anàlisi Comparativa i Selecció de la Solució
El primer pas és decidir quina eina utilitzarà EverPia. Heu de fer una anàlisi de mercat i presentar un breu informe comparatiu.
Tasques:
Investigar quatre alternatives populars d'assistència remota. (Exemples obligatoris: TeamViewer, AnyDesk, Google Remote Desktop. Heu d'afegir-ne una quarta de la vostra elecció.
Crear una Taula Comparativa que avaluï cada solució basant-se en els següents criteris clau:

- Facilitat d'ús (per al client): Requereix instal·lació? És portable? Com de senzill és per a un usuari no tècnic passar-nos l'ID?
- Disponibilitat (Sistemes Operatius): Funciona a Windows? macOS? Linux? (Vital per a EverPia, ja que donem suport a entorns mixtos).
- Model de Preu (Llicència): És gratuït per a ús comercial? Quant costa una llicència per a tècnic? Quines limitacions té la versió gratuïta?

<img width="594" height="413" alt="Captura de pantalla 2025-12-15 192953" src="https://github.com/user-attachments/assets/1b49bedd-650e-4422-a54d-01f8f6f2208c" />


### Presentar una Recomanació: Basant-vos en la vostra taula, heu de recomanar oficialment una de les eines per a l'adopció a EverPia, justificant per què és la millor opció (equilibri entre facilitat, funcionalitat i cost).

La meva recomanació d'elecció d'una eina de control remot per a EverPia és AnyDesk, perquè es una eina que tenint en compte la resta, és la més sencilla d'utilitzar tant per el tecnic com per a el usuari, a més és una eina que he utilitzar en alguna ocasió.

## Fase 2: Creació de les Guies d'Ús (Documentació)
Un cop heu seleccionat l'eina a la Fase 1, heu de crear la documentació oficial per al seu ús. Aquesta documentació és crucial i ha de tenir dos enfocaments diferents:

### Guia 1: Manual per al Tècnic (Intern d'EverPia)
El primer que hauras de fer serà instal·lar AnyDesk al teu ordinador desde la seva web oficial. Hi ha diferents tipus de descargues, la gratuïta, que té algunes limitacions i les de pagament que solen ser per a empreses.

<img width="1901" height="944" alt="Captura de pantalla 2025-12-15 193950" src="https://github.com/user-attachments/assets/3427d9a0-d0eb-4c7c-829c-5e90d1ac120b" />

<img width="1905" height="942" alt="Captura de pantalla 2025-12-15 194032" src="https://github.com/user-attachments/assets/c1b38f1b-00f0-4626-8c32-4716735b9bf2" />

---
Al obrir AnyDesk, veuras en la part superior uns números, que això es el teu número d'identificació. Aquest número també ho tenen els clients i serveix per poder convidar-los a una sessió remota.

<img width="1436" height="772" alt="Captura de pantalla 2025-12-15 200203" src="https://github.com/user-attachments/assets/79476521-3921-475c-b38b-daf387b67872" />

---
Per poder convidar als clients a una sessió remota, el que has de fer es donar clic al botó de invitar que esta a la dreta del ID i hauras de dirli al client que et digui el seu ID

<img width="1011" height="544" alt="image" src="https://github.com/user-attachments/assets/a724676e-4727-4284-801f-576ce97b3992" />

<img width="440" height="248" alt="Captura de pantalla 2025-12-15 194844" src="https://github.com/user-attachments/assets/30a59158-a064-4dca-bd1f-5b23518aaad9" />

---
Un cop el client t'accepti la sessió ja podras controlar el seu ordinador. A dins del control tens diferents funcions a dalt a la dreta mitjançant diferents icones, com per exemple xaitexar eamb ell, canviar de pantalla si en té més d'una, finalitzar o reiniciar la sessió, etc.

<img width="322" height="24" alt="Captura de pantalla 2025-12-15 200822" src="https://github.com/user-attachments/assets/0fee5c04-1a30-45fa-bddb-781e7af7a068" />

---
### Guia 2: Manual per al Client (Usuari Final)

Aquesta guia és la que enviarem als nostres clients quan tinguin una incidència. Ha de ser extremadament simple, visual i no tècnica.
---
El que hauras de fer primer de tot serà instal·lar una aplicació perquè el tecnic pugui controlar el teu ordiandor, que es AnyDesk des de la seva web oficial. La versió gratuïta ja et servirà.

<img width="1901" height="944" alt="Captura de pantalla 2025-12-15 193950" src="https://github.com/user-attachments/assets/aff6d536-5cba-4d4a-bab9-8fda379f2c23" />

---
Per poder obrir la aplicació, tens que mirar que s'hagi instal·lar en la fretxita de descarregues a dalt a la dreta. Si s'ha instal·lar, dones doble clic sobre ell.

<img width="330" height="235" alt="Captura de pantalla 2025-12-15 201518" src="https://github.com/user-attachments/assets/ebbb8058-713c-4c1f-924d-d4a7962dde40" />

---
Un a dins de l'aplicació, hauras de dirli al técnic el teu número d'identificació que et dona l'aplicació predeterminadament, que és el número que et surt a la part superior en el menú principal. 

<img width="1008" height="540" alt="image" src="https://github.com/user-attachments/assets/5e7aae6e-4633-44c0-9a39-26006f268da4" />

---
Quan el técnic t'envia la petició de control de sessió et sortira el que surt en la imatge i nomes has de donar a acceptar.

<img width="587" height="408" alt="Captura de pantalla 2025-12-15 200718" src="https://github.com/user-attachments/assets/0d44648e-e7c1-499f-9d41-b6c528e93066" />

---
Un cop iniciada la sessió, a dalt a la dreta tindràs diferents icones amb funcions, com per exemple xaitejar amb el técnic.

<img width="322" height="24" alt="Captura de pantalla 2025-12-15 200822" src="https://github.com/user-attachments/assets/3de82e5c-7423-4804-a968-7024bdd8a9bb" />

I això és tot el que habias de saber.



