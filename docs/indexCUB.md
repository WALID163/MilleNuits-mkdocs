# Ateliers de Professionnalisation (AP) - BTS SIO
## 🏢 Contexte : Entreprise CUB

Ce dépôt regroupe l'ensemble des productions réalisées dans le cadre des Ateliers de Professionnalisation (AP) du BTS SIO.

## 🎯 Objectif d'apprentissage

L'objectif pédagogique est de placer les étudiants dans une situation professionnelle simulée, reproduisant les exigences d'une Direction des Systèmes d'Information (DSI) d'une entreprise en pleine croissance.

En tant que techniciens supérieurs, nous intervenons au sein de l'équipe SIP (Service Informatique de Proximité) sur l'évolution du Système d'Information (SI) de CUB, entreprise spécialisée dans l'incubation de startups.

## 🏗️ Présentation de l'entreprise

Née en décembre 2010, CUB est une entreprise spécialisée dans l'incubation de startups partageant les mêmes valeurs de solidarité et de développement durable. Au travers de sa plate-forme web, CUB permet à des professionnels d'accéder à des espaces de travail dédiés : salles de réunion, de formations ou de séminaires.

Le concept novateur de CUB repose sur une démarche collaborative de type « BtoB » : CUB propose aux entreprises qui disposent d'espaces inoccupés de les louer à l'heure ou à la journée.

Armand Zaks, Michèle Ribez et Quentin Reynaud, les trois fondateurs, sont partis d'un double constat :
- en Île de France, 6 millions de m² de bureaux sont vacants ;
- en France, plus de 100 000 personnes travaillent ou ont déjà travaillé en espace de coworking. La France se classe au 6ème rang mondial pour le nombre d'espaces, et la pratique du coworking devrait continuer à progresser.

Forte d'une croissance très rapide, CUB fait une levée de fonds de 1,2 millions d'euros en 2016 et développe son activité pour atteindre sa dimension actuelle d'incubateur.

À la différence d'une pépinière d'entreprises classique, CUB s'adresse à des sociétés très jeunes, ou encore en création, pour leur apporter un appui lors des premières étapes de la vie de l'entreprise. Outre un parc de près de 200 m² mis à disposition des jeunes entrepreneurs, l'incubateur offre des services logistiques et d'infrastructures mutualisés, un accompagnement professionnel de conseil et de financement personnalisé aux porteurs de projets liés au digital, aux applications mobiles et au e-commerce.

CUB met à disposition de ses clients un ensemble de solutions techniques d'accès dans un millier de salles de réunion situées dans une quarantaine de villes différentes. Les ressources et outils du Web 2.0 qui permettent aux entreprises de gérer leurs contenus et leurs connaissances de manière sécurisée sont accessibles indépendamment via des prestataires de type informatique dans les nuages (cloud computing) : partage de fichiers, gestion de projet, réseau social d'entreprise, wiki d'entreprise, etc.

## 🌐 Environnement Technique

Le siège social de CUB est situé à Paris. Des agences sont implantées dans plusieurs grandes villes internationales :

- Anvers
- Barcelone
- Hong-Kong
- Los Angeles

La Direction des Systèmes d'Information (DSI), située à Paris, participe étroitement aux choix stratégiques de CUB. Elle a pour mission de définir et mettre en œuvre la politique informatique en accord avec la stratégie générale et ses objectifs de performance.

Chaque agence dispose d'une adresse IPv4 publique propre et nominative. Pour cela, l'entreprise CUB a demandé auprès du RIPE NCC l'obtention d'un numéro d'AS et d'un préfixe IPv4 : `192.36.253.0/24`. Elle est donc considérée comme un LIR (Local Internet Registry).

Le siège social est le cœur du système d'information interne de CUB, mais un service informatique de proximité (SIP) est présent sur chaque agence. Le SIP est responsable de l'assistance aux utilisateurs locaux et de la maintenance des ressources locales (infrastructure réseau et serveurs). Le SIP prend également en charge des projets qui concernent ponctuellement leur site.

## 🛠️ Domaines d'Intervention

Les missions évoluent au fil du temps pour couvrir les piliers majeurs de l'informatique d'organisation :

| Domaine | Actions réalisées |
|---|---|
| Administration Système & Réseau | Remplacement des pare-feu stateful PFSense par une solution UTM (Unified Threat Management) Stormshield. |
| Cybersécurité | Lutte contre le malware Emotet (cheval de Troie diffusé par mail et failles SMB), gestion des menaces informatiques. |
| Services | Mise en œuvre et administration d'un nouveau dispositif de sécurité dans chacune des agences. |

## 🦠 Définition du projet auquel vous allez participer

Le malware **Emotet** est un cheval de Troie qui se diffuse par mail (capacité à récupérer des listes de contacts et envoi de mail d'hameçonnage avancé) et par des failles de sécurité liées au protocole de partage de fichiers SMB de Microsoft. Il permet de récupérer des mots de passe, des listes de contact. Il sert actuellement à installer d'autres outils malveillants spécialisés dans la récupération d'informations bancaires.

Emotet a touché un nombre important d'entreprises françaises en 2020, ce qui a conduit l'ANSSI à publier un bulletin d'alerte. Ainsi, le service RSSI de l'entreprise CUB envisage le remplacement des pare-feu stateful vieillissants PFSense par une solution de sécurité unifiée (UTM) de l'entreprise française Stormshield afin d'améliorer la gestion des menaces informatiques au sein de la société.

Aujourd'hui, vous travaillez dans l'équipe SIP des différentes agences en tant que technicien systèmes et réseaux. Vous serez notamment en charge de la mise en œuvre d'un nouveau dispositif de sécurité dans chacune des agences nommé UTM (Unified Threat Management) émanant de la société française Stormshield spécialisée en sécurité des réseaux et des systèmes d'information. L'administration de cet équipement se fera exclusivement par le biais du réseau local de l'agence où vous avez été affecté.

## 📄 Documentation associée

L'architecture du réseau CUB est fournie dans la documentation ci-après :

- **Document A** – Architecture simplifiée du réseau CUB
- **Document B** – Plan d'adressage du réseau CUB
- **Document C** – Schéma réseau physique du réseau CUB
- **Document D** – Liste des serveurs présents sur le site du siège
