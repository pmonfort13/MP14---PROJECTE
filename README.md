# MP14
# MP14-PROJECTE
# INDEX

- ## PREPARACIÓ

  - [Anàlisi de riscos](#anàlisi-de-riscos)
  - [Contracte simbòlic i delimitació de l’abast](#doc-pla-director-de-seguretat)

- ## FASE RECONEIXEMENT

  - Consulta API Shodan amb Python
  - The Harvester Python
  - Més OSINT

- ## AUDITORIA DE SERVEIS

  - Escaneig
  - SSH
  - Enumeració
  
- ## FUNCIONALITATS AFEGIDES

  - Bot Telegram amb Python
  - Crear un contenidor Docker

- ## PLA DE MILLORA

- ## LANDING PAGE


---

# PREPARACIÓ

## Anàlisi de Riscos

En aquest apartat, realitzarem un anàlisi dels següents elements: actius, amenaces, delimitació, probabilitat, impacte i risc. Això ens ajudarà a determinar els objectius i les prioritats de la nostra auditoria, així com el seu abast i seqüència general per a cada empresa.

Per a això, utilitzarem dos tipus de documents:

### Document d'Anàlisi de Riscos

Aquest document definirà els registres, prioritats i classificacions de les iniciatives:

- Identificador: identifica cada cas.
- Títol: acció.
- Descripció: breu descripció del què fa l'acció.
- Responsable: persona encarregada.
- Tipus: categoria (Organitzativa, Tècnica i Física).
- Cost: el cost a assumir per l’empresa (Baix, Mitjà, Alt).
- Prioritat: necessitat de realitzar la tasca (Baix, Mitjà, Alt).

[Enllaç al document d'anàlisi de riscos](https://docs.google.com/spreadsheets/d/176OdSnzK3n5jHQtwUypUWkya4u1JjleQEpcceXBVcrw/edit#gid=0)



## Doc. Pla Director De Seguretat

- No

---

# FASE RECONEIXEMENT

## Eina API de Shodan:
- Hem d’importar l’eina Shodan a l’escript per poder-la implementar al nostre projecte:

![foto](../fotos/image1.jpg)

- L’escript de shodan està format per una funció principal funcioshodan() 
a la qual importem la nostra API de shodan, que hem aconseguit regsitrant-nos a la web prèviament:

![foto](../fotos/image2.jpg)

- Dins la funció principal, trobem 3 funcions que fan cadascuna de les 3 tasques demanades:

![foto](../fotos/image3.jpg)

- La primera funció és show_ip_info(), a la qual li passem el paràmetre ip, aquesta utilitza la funció .host() de shodan que ens dona un recull de tota la  informació a partir d’una adreça ip:

![foto](../fotos/image4.jpg)

aquesta informació la guardem a una variable “ipinfo” i seguidament la tractem per treure-la més ordenada i ja filtrada per natros juntament amb una llista “resultatf” què és on es va guardant la informació per després escriure-la al fitxer de resultat de l’aplicació.

Primer fem un print per indicar que mostrem els noms de domini, i amb un for in recorrem els ítems de la variable en busca de algun que contingui l’string “domains” i l’imprimim per pantalla quan coincideix.
Després d’imprimir-lo per pantalla, el guardem a la llista per després retornar-la i desar-la al fitxer:

![foto](../fotos/image5.jpg)

La segona part de la funció, filtra per ports oberts i fa també un print amb el títol i després amb un for in busca coincidències de “ports” i les imprimeix i les desa a la llista.
Finalment fa un return de la llista per a després poder afegir el seu contingut al fitxer de resultat final

![foto](../fotos/image6.jpg)


- La segona funció és show_services(), a la qual li passem també el paràmetre ip:

![foto](../fotos/image7.jpg)

aquesta utilitza la funció .host() de shodan que ens dona un recull de tota la  informació a partir d’una adreça ip,

![foto](../fotos/image8.jpg)

aquesta informació la guardem a una variable “ipinfo” i seguidament la tractem per treure-la més ordenada i ja filtrada per natros juntament amb una llista “resultatf” què és on es va guardant la informació per després escriure-la al fitxer de resultat de l’aplicació.

Però en aquest cas guardem els ports i el banner per mostrar els serveis que s'executen en cada port.
Després d’imprimir-lo per pantalla, el guardem a la llista per després retornar-la i desar-la al fitxer:

![foto](../fotos/image9.jpg)

- Per últim tenim un except per que en cas de error durant el codi fer un print de “Error”

![foto](../fotos/image10.jpg)

## The Harvester

L’escript de The Harvester esta format per una funció principal the_harvester_script() juntament amb el de guardar_informacio():

![foto](../fotos/image11.jpg)

![foto](../fotos/image12.jpg)

El primer que fa la funció és cridar l’eina TheHarvester amb el parametre “-h” per mostrar l’ajuda i veure els parametres que li podem passar:

![foto](../fotos/image13.jpg)

Seguidament ens demana amb 3 inputs, primer el domini o adreça sobre el que executar, font d’on volem que es faigue la busqueda i per últim opcions extra que volem que s’executin amb l’escript:

![foto](../fotos/image14.jpg)

Un cop tenim els paràmetres guardats en variables executem l’eina, aquesta vegada amb els paràmetres que hem guardat i desant el resultat a la variable “harvest”:

![foto](../fotos/image15.jpg)

Formata la sortida de la variable i fa un print per veure el resultat de l’escaneig:

![foto](../fotos/image16.jpg)

Per últim ens demana si volem guardar el resultat al fitxer ‘inf.txt’

![foto](../fotos/image17.jpg)

## Més OSINT -- INFOGA:

Com a eina extra de OSINT hem decidit utilitzar *INFOGA*, una eina per recopilar informació de comptes de correu electrònic de diferents fonts públiques (motors de cerca, servidors de claus PGP). 
És una eina senzilla, però molt efectiva per a les primeres etapes d'una prova de penetració o simplement per conèixer la visibilitat de la vostra empresa a Internet.

- L'script d'infoga consta d'una funció principal "infoga_script()" la qual conté tota la execució del programa amb les diferents opcions, formata la sortida i la guarda i un altra funció que és la de guardar el resultat en un document:

![foto](../fotos/image18.jpg)

La funció comença amb la execució amb l'eina subprocess de la comanda "infoga -h" per mostrar com s'utilitza l'eina i els diferents paràmetres i fa uns prints amb unes capçaleres de l'eina:

![foto](../fotos/image19.jpg)

Seguidament ens demana amb 3 inputs, primer el domini o adreça sobre el que executar la eina, font d’on volem que es faigue la busqueda i per últim opcions extra que volem que s’executin amb l’escript.
Després executa la comanda amb els parametres que li hem passat:

![foto](../fotos/image20.jpg)

Guardem el resultat de la comanda en una variable "infoga_output" i fem un printper a que es mostri el resultat per pantalla:

![foto](../fotos/image21.jpg)

Per últim ens pregunta si volem guardar el resultat en un fitxer i en cas positiu, utilitza la funció "guardar_informacio()" per desar-ho al document _inf.txt_ 

![foto](../fotos/image22.jpg)

---

# AUDITORIA DE SERVEIS
## Escanneig

Dintre aquest apartat, ens demanen crear una funció per realitzar un escaneig amb l’eina nmap.Aquesta funció, té com objectiu ajudar a descobrir els hosts disponibles de la xarxa, els ports oberts que te cada host, llistar les versions d’un o més ports d'algun host i llistar les vulnerabilitats d’un o més serveis.

Per elaborar aquesta part, tenim una funció que contingui el codi a executar:

![foto](../fotos/image23.jpg)

Dintre d’aquesta, implementarem un While que permet seleccionar entre diverses opcions al usuari.També farem un print per mostrar per pantalla les funcions disponibles i com executar-les:

![foto](../fotos/image24.jpg)

Finalment, creem una variable ‘env’ com a input per demanar a l'usuari que fiqui un número dintre el rang indicat per seleccionar una de les opcions indicades.Per correspondre  el input, utilitzem if i elif per importar i executar el mòdul seleccionat:

![foto](../fotos/image25.jpg)

#### En aquest cas, l’eina d’escanneig disposa de 4 funcions:

- ##### Xarxa():
Dintre, crearem la funció guardar_informacio_fitxer(informacio) per desar el resultat de l'execució al fitxer ‘inf.txt’:

![foto](../fotos/image26.jpg)

Crearem un altra funció anomenada xarxa() amb un input per preguntar la xarxa que vulgui l’usuari (específicant com ho ha de posar).Amb la IP introduïda, s’executa “nmap -sP” sobre la IP de xarxa ficada i acte seguit es captura la sortida:

![foto](../fotos/image27.jpg)

Finalment, assignem la variable “lineas” on separarem la sortida i preguntarem si vol guardar aquesta informació.En cas de que fiqui “si”, cridarem a la funció “guardar_informació_fitxer” per guardar el resultat obtingut:

![foto](../fotos/image28.jpg)

- ##### Ports():

Importem els mòduls necessaris i definim de nou la funció per guardar la informació al fitxer “inf.txt”:

![foto](../fotos/image29.jpg)

 Definim la funció de ports(), dintre preguntarem la IP a l’usuari i executem “nmap -p-” sobre la IP.Després, es guarda el resultat separat per linies a la variable “lineas”:

![foto](../fotos/image30.jpg)

Finalment, podem mostrar el resultat per pantalla i preguntar si vol guardar el resultat cridant la funció definida anteriorment:

![foto](../fotos/image31.jpg)

- ##### Versions():

Imortem els mòduls requerits  i definim de nou la funció per guardar la informació al fitxer “inf.txt”:

![foto](../fotos/image32.jpg)

Definim la funció versions(), dintre preguntem la IP i el port o rang de ports per executar “nmap -sV -p” sobre la IP i els ports.Després guardem el resultat separat per linies a la variable “lineas”:

![foto](../fotos/image33.jpg)

Finalment, preguntem si vol guardar el resultat i cridem a la funció guardar_informacio(lineas) definida anteriorment:

![foto](../fotos/image34.jpg)

- ##### Vuln():

Imortem els mòduls requerits  i definim de nou la funció per guardar la informació al fitxer “inf.txt”:

![foto](../fotos/image35.jpg)

Definim la funció vuln(), dintre demanem una IP i els ports a escanejar per executar “nmap -sV -p port –script=vuln” i guardar el resultat a la variable “lineas”, separat per línies:

![foto](../fotos/image36.jpg)

Finalment, preguntem si vol guardar la informació i cridem a la funció guardar_informacio(lineas) definida anteriorment:

![foto](../fotos/image37.jpg)

---

## SSH Audit

- Dintre l’apartat de ssh, ens demana implementar l’eina ‘ssh-audit’ al nostre arsenal d'auditoria.Per lo que ens dirigim al seu link de descarga a github i ens baixem ssh-audit:

![foto](../fotos/image38.jpg)

[**REPOSITORI DE L'EINA**](https://github.com/jtesta/ssh-audit)

Un cop baixat, el descomprimim i l’enviem a la ruta del projecte:

![foto](../fotos/image39.jpg)

![foto](../fotos/image40.jpg)

Un cop dintre el projecte, ens interessa el seu executable ‘ssh-audit.py’:

![foto](../fotos/image41.jpg)

A l’apartat d'escanneig, afegim una entrada per ssh-audit i creem un nou document de python per la implementació de l’eina:

![foto](../fotos/image42.jpg)

![foto](../fotos/image43.jpg)

![foto](../fotos/image44.jpg)

Dintre ‘sshaudit.py’, primer creem la funcio ‘guardar_informacio(info)’ per desar la informació al fitxer ‘inf.txt’:

![foto](../fotos/image45.jpg)

Creem la funció sshaudit(), dintre demanem la IP a l'usuari i executem l’eina ssh-audit.py indicant la ruta on esta guardat sobre la IP introduïda.Després, guardem el resultat a la variable ‘output’, separat per linies: 

![foto](../fotos/image46.jpg)

Finalment, fem un print per mostrar el resultat per pantalla i preguntem si es desitja guardar el resultat cridant a la funció definida anteriorment guardar_informacion(output):

![foto](../fotos/image47.jpg)

---

## Enumeració

- L'eina d'enummeració que hem utilitzat el Enum4Linux, la qual s'instal·La amb snap, però en el moment de crear el docker ens va donar errors ja que no funciona amb snap i enlloc d'aquesta eina, hem utilitzat un repositori de github anomenat "enum4linux-ng" descarregant-lo i executant-lo amb python.

L'esript consta d'una funció principal "enum4linux_tool()" de la qual penjen  dos funcions:
La primera "print_enum4linux()" és on fem un print de l'ajuda de l'eina i mostrem tots els paràmetres que se li poden passar a l'eina

![foto](../fotos/image48.jpg)

La segona funció "run_enum4linux()" és la que s'encarrega de 

![foto](../fotos/image49.jpg)



![foto](../fotos/image50.jpg)



![foto](../fotos/image51.jpg)



![foto](../fotos/image52.jpg)


