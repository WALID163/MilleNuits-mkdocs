# SP4 - Mission 2 : Création d’un sous-réseau développeurs avec accès Wi-Fi sécurisé et mise en placed’un portail captif 

**Auteur :** Walid
**Projet :** Mille nuits
---
## 1. Mise en place du point d'accès 

L'objectif est de configurer une borne Wi-Fi sécurisée pour le personnel de développement.

### Prérequis 
* La création d'un nouveau **VLAN Dev**.
* Un **switch** réseau.
* Un **point d'accès** pour permettre la connexion au VLAN DEV.

### Installation et Configuration
* **Accès à l'interface** : Créer un sous-réseau temporaire dans la plage par défaut de la borne ($192.168.0.50$) pour accéder à l'interface d'administration.
* **Paramétrage IP** : Changer l'adresse IP de la borne pour l'intégrer au **VLAN DEV**.
* **Sécurité SSID** : Désactiver la diffusion du nom du réseau (**SSID broadcast → DISABLE**) pour forcer une connexion manuelle par nom exact.
* **Service DHCP** : Activer le serveur DHCP sur le point d'accès pour attribuer automatiquement des adresses IP aux postes développeurs dans la bonne plage réseau.

### Paramètres sans fil (Wireless Settings)
| Paramètre | Valeur configurée |
| :--- | :--- |
| **Mode** | Access Point  |
| **Authentification** | WPA-Auto-Personal  |
| **Cipher Type** | AUTO |
| **SSID Broadcast** | Disable (préconisé) |

---

## 2. Isolement du sous-réseau DEV 

Pour sécuriser l'infrastructure, le sous-réseau des développeurs doit être isolé via des listes de contrôle d'accès (ACL) configurées sur le routeur.

### Configuration de l'ACL
L'ACL nommée `DEVELOPPEUR` définit les règles suivantes :
* **Accès DMZ autorisé** : Les communications ICMP et TCP sont permises entre le réseau dev ($172.40.2.144/28$) et la DMZ ($192.168.51.0/24$).
* **Communication Interne** : Le trafic IP est autorisé au sein du propre sous-réseau des développeurs.
* **Interdiction stricte** : Toutes les autres communications sont bloquées par la règle finale `deny ip any any`.
