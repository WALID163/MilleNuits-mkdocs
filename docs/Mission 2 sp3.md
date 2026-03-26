----
# Mise en place du serveur DHCP sous Linux

Ce guide détaille les étapes pour installer et configurer un serveur DHCP à l'aide du paquet **ISC DHCP** sur une machine virtuelle (Debian, Ubuntu...).

**Auteur :** Walid
**Projet :** Mille nuits
----
## Table des matières

1.  [Prérequis](#prérequis)
2.  [Installion du service](#installation-du-service)
3.  [Configuration de l'interface réseau](#configuration-de-l'interface-réseau)
4.  [Configuration des étendues](#configuration-des-étendues)

## 1. Prérequis
* Disposer d'une machine virtuelle Linux.
* Avoir accès aux paramètres réseau pour l'installation.
* Posséder les droits `sudo` sur la machine.

---

## 2. Installation du service
Lancez l'installation du paquet via la commande suivante :
```bash
sudo apt install isc-dhcp-server
```

---

## 3. Configuration de l'interface réseau
Avant de démarrer le service, vous devez désigner l'interface réseau sur laquelle le serveur doit écouter.

1.  **Ouvrez le fichier par défaut :**
    `sudoedit /etc/default/isc-dhcp-server`
2.  **Activez le fichier de configuration :** Décommentez la ligne `#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf`.
3.  **Spécifiez l'interface :** Localisez la variable `INTERFACESv4` et renseignez le nom de votre carte réseau (ex: `"ens3"`).
    > `INTERFACESv4="ens3"`

---

## 4. Configuration des étendues (dhcpd.conf)
Le paramétrage des réseaux et des baux se fait dans le fichier principal :
`sudoedit /etc/dhcp/dhcpd.conf`

### Paramètres globaux
Vous pouvez définir des options communes à tous les réseaux :
* **Domaine :** `option domain-name "votre-domaine.fr";`
* **DNS :** `option domain-name-servers ns1.example.org, ns2.example.org;`
* **Durée des baux :** * Défaut : `345600` (4 jours)
    * Maximum : `691200` (8 jours)

### Déclaration d'un sous-réseau
Pour créer une étendue d'adresses, utilisez le bloc suivant :

```bash
# Définition du sous-réseau et du masque
subnet 192.000.00.0 netmask 255.255.255.0 {
  
  # Plage d'adresses IP distribuées
  range 192.000.00.1 192.000.00.50;
  
  # Serveurs DNS spécifiques et Passerelle
  option domain-name-servers 150.000.00.0, 8.8.8.8;
  option routers 192.000.00.254;
  
}
```

*Note : Cette structure est à répéter pour chaque étendue réseau nécessaire.*

Enfin, il faut redémarrer le serveur :
`sudo systemctl restart isc-dhcpd-server.service`

---
