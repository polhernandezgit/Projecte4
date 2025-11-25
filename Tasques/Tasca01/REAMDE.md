# T01: DRP: còpies de seguretat. Estudi cas client (treball cooperatiu)

## Introducció
La primera hora el vostre responsable de seguretat us presenta el tema de les còpies de seguretat a partir d’un material didàctic. A continuació, caldrà que treballeu els aspectes del tema i ho fareu mitjançant una dinàmica cooperativa.

## Presentació del cas client
"Muntatges i Serveis Tècnics SL" és una petita empresa dedicada a la instal·lació i manteniment d'equips industrials.

## Infraestructura Tècnica:
· Servidor de Fitxers (Ubuntu Server): Conté tota la documentació crítica:
- Documents de Projectes: Plànols, especificacions tècniques (300 GB, creixement moderat).
- Bases de Dades (Comptabilitat i Clients): Crítiques i d'ús diari (20 GB, canvi constant).
- Carpetes Personals dels Usuaris: Per a la feina diària (100 GB).
· 10 Equips Clients (Windows 10/11): Els usuaris treballen majoritàriament amb fitxers del servidor, però alguns tècnics guarden de forma temporal informes i altres arxius importants a la carpeta Documents.
· Connexió a Internet: Fibra òptica de 600 Mbps (simètrica).

## Requisits de Recuperació:
· Temps de Recuperació (RTO): Les dades de Comptabilitat/Clients han d'estar disponibles en menys de 4 hores.
· Pèrdua de Dades Admesa (RPO): Es pot admetre una pèrdua màxima de 24 hores per a la majoria de dades, però les dades de Comptabilitat/Clients no poden perdre més de 4 hores de treball.
· Retenció: Cal guardar les dades amb un historial d'almenys un mes.

# Fase 1: Treball individual
De forma individual, heu de donar resposta a les següents preguntes basant-se en el cas pràctic:

## 1. Què copiar? (Priorització): Quines són les dades més crítiques del servidor? Cal fer còpia dels 10 equips clients? Justifica-ho.
El que s’hauria de copiar seria principalment les dades crítiques del servidor que són:
- Bases de Dades.
- Documents de Projectes.
- Carpetes Personals dels Usuaris.ç
Cal fer les còpies de totes les dades però parcialment, perquè hi ha treballadors que guarden informes temporals en documents que poden ser importants.

## 2. Periodicitat i Tipus de Còpia: Proposa un calendari bàsic per a la setmana (Diari/Setmanal/Mensual) i quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) per a les dades crítiques.
Cada dade s’ha de fer còpies de seguretat cada x temps, depenent de si será completa, diferencial o incremental.

Base de dades ( crític ):
- Còpia completa setmanal.
- Còpia incremental cada 4 hores.

Documents de projecte:
- Còpia completa setmanal.
- Còpia diferencial diaria.

Carpetes personals dels usuaris:
- Còpia completa setmanal.
- Còpia incremental diaria a la nit.

## 2. Mitjans i Ubicació: Quin tipus de mitjà de còpia utilitzaries (Discs durs externs, NAS, Cloud, Cintes)? On s'hauria de guardar físicament la còpia més recent (Regla 3-2-1).
El tipus de mitjà de còpia que utilitzare serà de NAS i cloud, perquè el NAS sol ser ideal per recuperacions ràpides o snapshots freqüents i el cloud perquè té gran seguretat en cas d'incendi, robatori, etc o que té redundancia geogràfica.

Les còpies més recents com les incrementals s’haurien de guardar en el NAS per tenir un RTO ràpid i una copia diaria o semanal al núvol.

# Fase 2: Treball per parelles
Treballant per parelles:

1. Discussió i Consens: Comparen les seves respostes individuals (Fase 1).
2. Elaboració d'una Proposta Unificada: Heu de consensuar i dissenyar el vostre propi Esquema 3-2-1 de Còpies (3 còpies, 2 mitjans, 1 fora de lloc) basat en els requisits del cas.

| **Element**                  | **Proposta de la Parella**                                               | **Justificació**                                                                                                                                                                                                                                                                             |
|-----------------------------|---------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Dades Crítiques**         | - Base de dades<br>- Documents de projectes                              | La base de dades és una informació única, insubstituïble i sensible, i està en canvi constant, per això ha de tenir la màxima prioritat a l’hora de fer còpies de seguretat. Qualsevol pèrdua podria afectar el funcionament diari de l’empresa.<br><br>Els documents de projecte tenen una prioritat menor però continuen sent importants, ja que formen part de la documentació de treball dels tècnics i representen un gran volum d’informació que cal conservar. |
| **Periodicitat (BD)**       | Còpies setmanals i cada 4 hores per a la BD; setmanals i diàries per a documents | Cal fer còpies setmanals i cada 4 hores per a la base de dades, ja que és la informació més crítica i la que canvia més sovint.<br><br>Per als documents de projectes, és convenient fer còpies setmanals i diàries, perquè tot i no ser tan crítics, continuen sent essencials per al treball diari. |
| **Tipus de Còpia (BD)**     | Incrementals per a BD; diferencials per a documents                      | Les còpies incrementals són ideals per a la base de dades perquè només guarden els canvis des de l’última còpia, permetent còpies més ràpides i freqüents.<br><br>Les còpies diferencials són adequades per als documents de projectes perquè no canvien tan sovint i faciliten la recuperació combinant la còpia completa i l’última diferencial. |
| **Mitjà 1 (Local)**         | NAS                                                                       | El NAS és viable perquè ofereix un equilibri entre seguretat i cost, permet còpies centralitzades, ràpides i fiables sense una gran inversió. |
| **Mitjà 2 (Extern)**        | Cloud                                                                     | El cloud és una alternativa adequada per la seva flexibilitat i viabilitat. |


# Fase 3: Treball en grup
1. Debat i Selecció: Cada parella presenta el seu esquema. El grup debat els pros i contres de cada proposta (cost, temps de recuperació, seguretat, simplicitat).
2. Disseny de la Política Final: El grup ha de redactar la Política de Còpies de Seguretat Definitiva que presentaran a l'empresa "Muntatges i Serveis Tècnics SL".

## Document Final (Fase 3)
El grup ha de generar un document amb els següents punts resolts:

1)  Dades Objecte de Còpia.
Quines dades es copien i amb quina freqüència (separant Servidor/Clients i crítiques/no crítiques).****

2) Cronograma Setmanal Detallat



