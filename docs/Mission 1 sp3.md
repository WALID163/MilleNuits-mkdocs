# SP3 — Mission 1 : Mise en place du serveur Windows Server 2019

**Boisseau Crys — 801**  
*Mille Nuits*

---

## Table des matières

- [Windows Serveur — Récapitulatif des tâches](#windows-serveur--récapitulatif-des-tâches)
- [Ajouter des rôles et fonctionnalités AD DS et DNS](#ajouter-des-rôles-et-fonctionnalités-ad-ds-et-dns)
- [Ajouter des unités d'organisation, groupes et utilisateurs](#ajouter-des-unités-dorganisation-groupes-et-utilisateurs)
- [Désactiver la récursivité sur le serveur DNS](#désactiver-la-récursivité-sur-le-serveur-dns)

---

## Windows Serveur — Récapitulatif des tâches

**Rôles à activer :**
- AD DS
- DNS ← Créer la zone `MNXX.lan` (XX = numéro de VLAN)

**Unités d'organisation à créer :**
- Visiteur
- Administratif
- Commerciaux
- Autres
- Production
- Logistique
- VenteEtudes

**Pour chaque unité d'organisation :**
1. Créer un **groupe**.
2. Créer **deux utilisateurs**.
3. Ajouter chaque utilisateur à son groupe.

**Désactiver la récursivité** sur le serveur DNS.

---

## Ajouter des rôles et fonctionnalités AD DS et DNS

1. Dans le **Gestionnaire de serveur**, cliquer sur **Gérer** → **Ajouter des rôles et fonctionnalités**.
2. Cocher les rôles **Serveur DNS** et **Services AD DS**, puis continuer jusqu'à l'installation.
3. Une fois installés, **finir de configurer l'AD DS** via la notification dans le Gestionnaire de serveur :
   - Sélectionner **Ajouter une nouvelle forêt**.
   - Saisir le nom de domaine racine (ex : `MN53.lan`).
   - Compléter les étapes jusqu'à la confirmation.
4. La machine **redémarrera** automatiquement.

---

## Ajouter des unités d'organisation, groupes et utilisateurs

Dans **Outils → Utilisateurs et ordinateurs Active Directory** :

Pour chaque service (Administratif, Commerciaux, Logistique, etc.) :

1. Faire un clic droit sur le domaine → **Nouveau → Unité d'organisation** → saisir le nom du service.
2. Dans l'unité d'organisation créée → **Nouveau → Groupe** → saisir le nom du groupe.
3. Dans l'unité d'organisation → **Nouveau → Utilisateur** → créer deux utilisateurs (ex : `Admin1`, `Admin2`).
4. Ouvrir chaque utilisateur → onglet **Membre de** → ajouter le groupe correspondant.

---

## Désactiver la récursivité sur le serveur DNS

1. Dans le **Gestionnaire de serveur**, aller dans **Outils → DNS**.
2. Faire un clic droit sur le nom du serveur → **Propriétés**.
3. Aller dans l'onglet **Avancé**.
4. Cocher **Désactiver la récursivité (désactive également les redirecteurs)**.
5. Cliquer sur **Appliquer** puis **OK**.
