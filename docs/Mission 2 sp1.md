# SP1 — Mission 2 : Mise en place de l'infrastructure réseau

**BOISSEAU Crys — JOUAL Walid — 801**  
*Mille Nuits*

---

## Table des matières

- [Commandes](#commandes)
  - [Configuration d'un VLAN](#configuration-dun-vlan)
  - [Configuration d'une interface SWITCH](#configuration-dune-interface-switch)
  - [Configuration des interfaces ROUTER/SWITCH – SWITCH/ROUTER](#configuration-des-interfaces-routerswitch--switchrouter)
  - [Configuration IP VLAN SWITCH](#configuration-ip-vlan-switch)
  - [Configuration IP ROUTEUR](#configuration-ip-routeur)
  - [Configuration NAT](#configuration-nat)
  - [Configuration d'une sous-interface ROUTEUR](#configuration-dune-sous-interface-routeur)
  - [Télécharger un fichier d'un ROUTEUR/SWITCH](#télécharger-un-fichier-dun-routeurswitch)
  - [Tftpd32 by Ph. Jounin](#tftpd32-by-ph-jounin)

---

## Commandes

### Configuration d'un VLAN

```
switch> en
switch# config t
switch(config)# vlan X
switch(config-vlan)# name xxxx
switch(config-vlan)# exit
```

---

### Configuration d'une interface SWITCH

**Mode ACCESS :**

```
Switch> en
Switch# config t
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan X
Switch(config-if)# no shutdown
Switch(config-if)# exit
```

---

### Configuration des interfaces ROUTER/SWITCH – SWITCH/ROUTER

**Mode TRUNK :**

```
Switch> en
Switch# config t
Switch(config)# interface gigabitEthernet0/0
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan X,X,X,X,X
Switch(config-if)# no shutdown
Switch(config-if)# exit
```

---

### Configuration IP VLAN SWITCH

```
Router> en
Router# config t
Router(config)# interface vlan X
Router(config-if)# ip address xxx.xxx.x.x 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

---

### Configuration IP ROUTEUR

```
Router> en
Router# config t
Router(config)# interface vlan X
Router(config-if)# ip address xxx.xxx.x.x 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

---

### Configuration NAT

```
Router> en
Router# conf t
Router(config)# access-list 1 permit xxx.xx.x.x 0.0.0.255
Router(config)# ip nat inside source list 1 interface fa0/1 overload
Router(config)# interface fa0/X
Router(config-if)# ip nat inside
Router(config-if)# exit
Router(config)# interface fa0/X
Router(config-if)# ip nat outside
Router(config-if)# exit
```

---

### Configuration d'une sous-interface ROUTEUR

```
Router> en
Router# conf t
Router(config)# interface fa0/x.x
Router(config-subif)# exit
```

---

### Télécharger un fichier d'un ROUTEUR/SWITCH

Avec le logiciel **Tftpd32 by Ph. Jounin**, votre PC sert de serveur TFTP pour communiquer avec le switch/routeur.

Le switch ou routeur doit avoir une IP sur un de ses ports pour communiquer avec le serveur TFTP. Pour un switch, il faut attribuer une IP à un VLAN.

**Télécharger des fichiers (depuis le switch/routeur vers le PC) :**

```
Switch/Router> en
Switch/Router# copy nomdufichier.extension tftp:
Address or name of remote host []? (adresse IP de votre PC)
Destination filename [nomdufichier.extension]? (nom souhaité sur le PC)
```

**Envoyer des fichiers (depuis le PC vers le switch/routeur) :**

```
Switch/Router> en
Switch/Router# copy tftp nomdufichier.extension
Address or name of remote host []? (adresse IP de votre PC)
Destination filename [nomdufichier.extension]? (nom du fichier à importer)
```

---

### Tftpd32 by Ph. Jounin

| Paramètre | Description |
|---|---|
| **Current Directory** | Emplacement des fichiers qui seront téléchargés ou importés |
| **Server interfaces** | IP de votre PC |

Lien pour le logiciel : [Releases · PJO2/tftpd64](https://github.com/PJO2/tftpd64/releases)
