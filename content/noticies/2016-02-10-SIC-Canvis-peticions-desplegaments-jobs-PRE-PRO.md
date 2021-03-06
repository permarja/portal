+++
date        = "2016-02-10"
title       = "Canvi al sistema d'obertura de peticions als jobs de desplegament a PRE/PRO de SIC"
description = "Fins el moment, les peticions de desplegament a entorns PRE/PRO que es demanaven mitjançant jobs de Jenkins SIC seguien l'antic model d'obertura de peticions: correu a la bústia de SAU. Amb l'entrada de Remedy, el mecanisme per a demanar desplegaments ha canviat."
sections    = ["Notícies", "home"]
categories  = ["sic"]
key         = "MARC2016"
+++

Fins el moment, les peticions de desplegament a entorns PRE/PRO que es demanaven mitjançant jobs de Jenkins SIC seguien l'antic model d'obertura de peticions: correu a la bústia de SAU.
Amb l'entrada de Remedy, el mecanisme per a demanar desplegaments ha canviat. Les aplicacions donades d'alta a Remedy han de demanar els desplegaments mitjançant l'obertura d'un tiquet de tipus canvi a l'eina.
L'equip de SIC ha treballat en l'adaptació dels jobs de desplegament a PRE/PRO per tal d'acollir-se al model de peticions de desplegament mitjançant Remedy.

Els jobs de desplegament a PRE/PRO de SIC adaptats a aquest sistema:

* Pujaran els artefactes a desplegar als servidors de CPD (aquest punt no canvia respecte al model anterior).
* Obriran un **canvi de tipologia “Desplegament” i en estat=”Draft”** a Remedy (no es requerirà passar prèviament per l'Atrium Impact Simulator) i com a Sol·licitant l'usuari que ha executat el job de desplegament. **L'usuari que executarà el job ha d'estar donat d'alta a GICAR i amb usuari autoritzat a treballar a ITSM Remedy. Si no és així, ITSM Remedy denegarà l'obertura del canvi** i el job finalitzarà amb error.
* Els valors dels camps 'Summary' i 'Notes' que figuraran al Draft del canvi, es correspondran amb els camps 'TITOL' i 'OBSERVACIONS' del job de Jenkins. Aquests s'indicaran amb un valor per defecte que l'usuari podrà editar. La informació sobre la ubicació on s'han pujat prèviament els artefactes a desplegar s'afegirà automàticament al camp ''Notes'.
* Una vegada creat el Draft, el job retornarà l'identificador de petició creada a Remedy. En paral·lel, ITSM Remedy enviarà una notificació d'obertura de tasca a la bústia de l'usuari que ha executat el job des del SIC.
* El Draft es generarà amb uns camps mínims. Posteriorment, qualsevol usuari del grup de gestió d’ITSM REMEDY associat al desplegament haurà d'accedir al Draft per completar la resta de dades (incloent el document amb les instruccions de desplegament) i aplicar la instrucció operativa vigent de Gestió de Canvis.


<center>![autoritzacions_peticions_responsables.png](/images/news/SIC-Jobs-peticions-Remedy.png)</center>

El canvi es va activar el dia **22 de Febrer** per als jobs d'aquelles aplicacions que ja es trobin dins Remedy. Els jobs de la resta d'aplicacions que encara no s'hagin integrat a Remedy mantindran l'antic sistema d'obertura de petició via correu a SAU.
En el moment que aquestes aplicacions s'afegeixin a Remedy, l'equip de SIC actualitzarà els seus jobs per tal que facin servir el model d'obertura de canvis via ITSM Remedy (els proveïdors no s'hauran de preocupar de demanar l'actualització dels jobs).

Per a qualsevol dubte relatiu a aquest canvi, podeu contactar amb SAU (sau.tic@gencat.cat / Consulta al servei 'FRAMEWORK SIC' de Remedy).
