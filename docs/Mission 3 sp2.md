# MILLENUITS SP2 – Mission 3 : Recherche et mise en place d'un outil de déploiement des postes

**Boisseau Crys — 801**  
*Mille Nuits*

---

## Table des matières

- [A.1 C'est quoi un outil de déploiement d'OS](#a1-cest-quoi-un-outil-de-déploiement-dos)
- [A.2 Pourquoi utiliser un outil de déploiement d'OS](#a2-pourquoi-utiliser-un-outil-de-déploiement-dos)
- [B.1 Comparaison des outils de déploiement d'OS](#b1-comparaison-des-outils-de-déploiement-dos)
- [B.2 Choix final de l'outil de déploiement d'OS](#b2-choix-final-de-loutil-de-déploiement-dos)

---

## A.1 C'est quoi un outil de déploiement d'OS

Un outil de déploiement de systèmes d'exploitation est une solution informatique qui automatise les processus d'installation, de configuration et de mise à jour de logiciels sur des appareils distants. Ces outils sont particulièrement utiles pour les grandes entreprises gérant une main-d'œuvre dispersée ou des services informatiques supervisant des appareils à distance.

---

## A.2 Pourquoi utiliser un outil de déploiement d'OS

| Avantages | Désavantages |
|---|---|
| Gain de temps (déploiement simultané sur plusieurs postes) | Mise en place initiale complexe |
| Automatisation des configurations et données | Infrastructure nécessaire |
| Standardisation des machines (même configuration partout) | Problèmes de compatibilité matériel selon le poste |
| Déploiement rapide après panne | Consommation réseau importante (bande passante) |
| Gestion centralisée depuis un serveur | Risque d'erreur massive si l'image est défaillante |

**Exemple concret :** pour 100 postes à configurer, il suffit d'en configurer un seul, de copier son image ISO et de la pousser sur tous les autres grâce à un outil de déploiement.

Les trois outils comparés sont : **FOG (Free Open-Source Ghost)**, **Clonezilla** et **Windows Deployment Services (WDS)**.

---

## B.1 Comparaison des outils de déploiement d'OS

| Critère | FOG | Clonezilla | WDS |
|---|---|---|---|
| Type d'imagerie | Bloc disque | Bloc disque | Fichier (WIM) |
| Interface | Web | Terminal | Interface Windows |
| PXE réseau | Oui | Possible | Oui |
| Automatisation | Élevée | Faible | Moyenne |
| OS supportés | Windows / Linux | Windows / Linux | Windows uniquement |
| Licence | Open source | Open source | Microsoft (payant) |

---

## B.2 Choix final de l'outil de déploiement d'OS

### WDS — Éliminé

Points positifs : supporte le PXE, type d'imagerie correct, automatisation acceptable.

Points négatifs : déploie uniquement Windows, appartient à Microsoft et est donc payant.

### Clonezilla — Éliminé

Points positifs : type d'imagerie correct, supporte Windows et Linux, open source.

Points négatifs : automatisation faible, interface en ligne de commande uniquement, PXE seulement possible.

### FOG — **Choix retenu** ✅

Points positifs : type d'imagerie correct, support PXE natif, interface Web, automatisation élevée, supporte Windows et Linux, open source.

**Conclusion : FOG est le choix retenu**, car il cumule le plus d'avantages et répond parfaitement aux besoins du déploiement en masse des postes.
