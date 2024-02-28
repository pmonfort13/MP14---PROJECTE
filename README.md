# MP14
# MP14-PROJECTE
# INDEX

## PREPARACIÓ

- [Anàlisi de riscos](#anàlisi-de-riscos)
- [Contracte simbòlic i delimitació de l’abast](#doc-pla-director-de-seguretat)

## FASE RECONEIXEMENT

- Consulta API Shodan amb Python
- The Harvester Python
- Més OSINT

## AUDITORIA DE SERVEIS

- Escaneig
- SSH
- Enumeració

## FUNCIONALITATS AFEGIDES

- Bot Telegram amb Python
- Crear un contenidor Docker

## PLA DE MILLORA

## LANDING PAGE


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
