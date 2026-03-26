# Fiche de recette — SP3 Mission 1 : Maquette avec et sans Wifi (D-LINK)

**Boisseau Crys — Joual Walid — 801**  
*Mille Nuits*

---

## Maquette sans Wifi

### Test 1 — Ping entre les sous-réseaux et les serveurs de la ferme de serveurs

| Champ | Détail |
|---|---|
| **Description du test** | Ping entre les sous-réseaux et les serveurs de la ferme de serveurs |
| **Résultat attendu** | Les serveurs de la ferme de serveurs renvoient un paquet |

**Réception :**
- [x] Reçu
- [ ] Reçu avec réserve
- [ ] Refusé

**Commentaire :** Les serveurs de la ferme de serveurs répondent par un paquet aux différents PC des différents sous-réseaux.

---

### Test 2 — Ping entre les sous-réseaux et le serveur Internet

| Champ | Détail |
|---|---|
| **Description du test** | Ping entre les sous-réseaux et le serveur Internet |
| **Résultat attendu** | Le serveur Internet renvoie un paquet aux sous-réseaux |

**Réception :**
- [x] Reçu
- [ ] Reçu avec réserve
- [ ] Refusé

**Commentaire :** Le serveur Internet répond par un paquet aux différents PC des différents sous-réseaux.

---

## Maquette avec Wifi

### Test 3 — Le portable Wifi Visiteur ping le serveur Internet

| Champ | Détail |
|---|---|
| **Description du test** | Le portable Wifi visiteur ping le serveur Internet |
| **Résultat attendu** | Le serveur Internet répond |

**Réception :**
- [x] Reçu
- [ ] Reçu avec réserve
- [ ] Refusé

**Commentaire :** Le serveur Internet répond par un paquet au portable Wifi visiteur.

---

### Test 4 — Le portable Wifi Commerciaux ping le serveur Internet

| Champ | Détail |
|---|---|
| **Description du test** | Le portable Wifi commerciaux ping le serveur Internet |
| **Résultat attendu** | Le serveur Internet répond |

**Réception :**
- [x] Reçu
- [ ] Reçu avec réserve
- [ ] Refusé

**Commentaire :** Le serveur Internet répond par un paquet au portable Wifi commerciaux.

---

## D-LINK physique

### Test 5 — Connexion au point d'accès avec un téléphone

| Champ | Détail |
|---|---|
| **Description du test** | Se connecter au point d'accès avec un téléphone |
| **Résultat attendu** | Le point d'accès demande un mot de passe et attribue une adresse IP dans la bonne plage automatiquement |

**Réception :**
- [x] Reçu
- [ ] Reçu avec réserve
- [ ] Refusé

**Commentaire :** Le point d'accès demande un mot de passe et attribue une adresse IP dans la bonne plage automatiquement au téléphone.
