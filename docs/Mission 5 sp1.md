# Mission 5 - Fiche recette pour GLPI

**Boisseau Crys — 801 — 06/11/2025**  
*Lycée Paul-Louis Courier — Le lycée de tous les parcours*

---

## Table des matières

- [1. Informations générales](#1-informations-générales)
- [2. Objet du test](#2-objet-du-test)
- [3. Pré-requis](#3-pré-requis)
- [4. Scénario de test](#4-scénario-de-test)

---

## 1. Informations générales

| Champ | Valeur |
|---|---|
| Projet | GLPI tickets |
| Version | GLPI 11 |
| Date | 27/11/2025 |
| Rédacteur | Boisseau Crys |

---

## 2. Objet du test

Vérifier que les utilisateurs **Utilisateur** et **Technicien** sont fonctionnels et peuvent rédiger et résoudre un ticket.

---

## 3. Pré-requis

- Compte test **Utilisateur** et **Technicien** sur GLPI
- Accès à l'interface Web de GLPI
- Navigateur

---

## 4. Scénario de test

**Objectif :** Se connecter au compte Utilisateur et soumettre un ticket sur l'interface web de GLPI.

### Étapes

1. Utiliser un navigateur et accéder à `(IpdelaMachine/glpi)` pour aller sur l'interface web de GLPI.
2. Se connecter avec le compte **Utilisateur** (pour les invités).
3. Rédiger un ticket et le soumettre.
4. Se connecter avec le compte **Technicien**.
5. Vérifier les tickets.
6. Résoudre le ticket soumis par le compte Utilisateur.

### Résultat attendu

Le ticket du compte **Utilisateur** est visible par le compte **Technicien** et peut être résolu par celui-ci.

### Résultat obtenu

✅ Le ticket est visible pour le compte **Technicien** et peut être résolu par celui-ci.
