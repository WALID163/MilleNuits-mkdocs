# SP1 Mission 4 – Choix d'un outil de gestion de tickets d'incidents adapté au BTS SIO

**Boisseau Crys — 801 — 06/11/2025**  
*Lycée Paul-Louis Courier — Le lycée de tous les parcours*

---

## Table des matières

- [A. Description des outils de gestion de tickets d'incidents](#a-description-des-outils-de-gestion-de-tickets-dincidents)
- [B. Analyse des outils de gestion de tickets d'incidents](#b-analyse-des-outils-de-gestion-de-tickets-dincidents)
- [C. Choix d'un outil de gestion de tickets d'incidents](#c-choix-dun-outil-de-gestion-de-tickets-dincidents)

---

## A. Description des outils de gestion de tickets d'incidents

### GLPI (Gestionnaire Libre de Parc Informatique)

Logiciel libre de gestion des services informatiques et d'assistance. Il permet aux entreprises de centraliser la gestion de leurs équipements, logiciels, licences et contrats. GLPI offre également des fonctionnalités telles que la gestion d'actifs, une base de données de gestion de configuration (CMDB) et un service d'assistance, le tout sur une seule plateforme.

### Lansweeper (ITAM)

Lansweeper est une solution ITAM qui aide les entreprises à mieux comprendre, gérer et protéger leurs appareils et réseaux informatiques. Elle permet de découvrir et d'inventorier tous les types d'actifs technologiques, de logiciels installés et d'utilisateurs, facilitant ainsi la gestion d'inventaire d'actifs informatiques et l'identification des risques d'attaques malveillantes. Lansweeper offre une vue globale du domaine informatique, comptabilise tous les points d'entrée potentiellement vulnérables et fait correspondre les vulnérabilités NIST à l'inventaire des actifs. Elle comprend également un service d'assistance. Cette solution est essentielle pour maintenir un inventaire à jour et précis de tous les actifs informatiques.

### osTicket

osTicket est un système de gestion de tickets d'assistance open source qui centralise et automatise les demandes d'assistance. Il permet de gérer, organiser et archiver toutes les demandes et réponses d'assistance dans une interface Web conviviale et multi-utilisateurs. Les fonctionnalités incluent des champs personnalisés, des réponses automatiques, des évits de collisions avec les agents, des formulaires de rubrique d'aide personnalisés, et la prise en charge des e-mails en texte enrichi ou HTML. osTicket est particulièrement adapté aux petites et moyennes entreprises et est disponible gratuitement.

---

## B. Analyse des outils de gestion de tickets d'incidents

### GLPI

GLPI est un outil open source permettant de centraliser la gestion des équipements, logiciels, licences et contrats, de gérer les actifs et une base de données CMDB, et surtout d'assurer un service d'assistance. GLPI est donc un très bon outil offrant beaucoup de fonctionnalités, disponible gratuitement et compatible avec Linux.

### Lansweeper (ITAM)

Tout comme GLPI, Lansweeper offre de nombreuses options : inventaire de tous les types d'actifs technologiques, vue globale d'un domaine informatique, et un service d'assistance. Cependant, Lansweeper n'est pas open source et est obtenu avec une licence perpétuelle à 0 €. Lansweeper est donc un bon outil compatible avec Linux, mais limité car non open source.

### osTicket

Comparé à GLPI et Lansweeper, osTicket est un outil de gestion de tickets d'incidents purement conçu pour cela. Il offre des fonctionnalités clés : réponses automatiques, formulaires de rubriques d'aide personnalisés et prise en charge des e-mails en texte enrichi ou HTML. Adapté aux petites et moyennes entreprises, osTicket est un outil efficace, open source et compatible avec Linux.

---

### Tableau comparatif

| Solution | Avantages | Désavantages |
|---|---|---|
| **GLPI** | Gratuit et open source · Hautement configurable · Inventaire IT · Populaire · Pour tous types d'entreprises | Interface moins moderne · Prise en main raide · Dépendance à la communauté pour le support |
| **osTicket** | Gratuit et open source · Base de connaissances intégrée · Prise en main rapide · Pour petites et moyennes entreprises | UI vieillissante · Fonctions avancées de reporting limitées · Dépendance à la communauté pour le support |
| **Lansweeper** | Partiellement gratuit · Populaire · Prise en main relativement rapide · Pour tous types d'entreprises | Non open source · Limité en fonctionnalités · Moins orienté ticketing |

---

## C. Choix d'un outil de gestion de tickets d'incidents

Après analyse des 3 outils, **Lansweeper** est éliminé en premier : il n'est pas open source et requiert une licence perpétuelle à 0 €, cette édition limitant par ailleurs les fonctionnalités.

Il reste donc **GLPI** et **osTicket**, tous deux gratuits et open source.

- Si l'on cherche quelque chose de **simple à utiliser**, la meilleure option est **osTicket** : facile à prendre en main et centré sur la gestion de tickets, malgré une UI vieillissante et une dépendance à la communauté pour le support.

- Si l'on cherche quelque chose de **complet**, **GLPI** est la meilleure option : gratuit, hautement configurable et open source, il offre énormément de fonctionnalités bien au-delà de la simple gestion de tickets, même si sa prise en main initiale peut être plus complexe.

**Conclusion : GLPI est le meilleur choix**, pour la richesse de ses fonctionnalités, son adaptabilité et sa popularité dans le milieu professionnel.
