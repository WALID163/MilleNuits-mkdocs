# BLOC 2 – Administration des systèmes

*Crys Boisseau 901 Walid Joual*

## Table des matières

- [Situation](#situation)
1. [Créer une VM à partir des indications ci-après](#1-créer-une-vm-à-partir-des-indications-ci-après)
2. [Vérifier la configuration IP de votre VM. Quel est votre constat ?](#2-vérifier-la-configuration-ip-de-votre-vm-quel-est-votre-constat-)
3. [Installer les drivers permettant la détection de votre carte réseau en utilisant les commandes PS suivantes](#3-installer-les-drivers-permettant-la-détection-de-votre-carte-réseau-en-utilisant-les-commandes-ps-suivantes)
4. [Vérifier la détection de votre carte réseau et réaliser les paramétrages suivants](#4-vérifier-la-détection-de-votre-carte-réseau-et-réaliser-les-paramétrages-suivants)
5. [Changer le nom de votre serveur](#5-changer-le-nom-de-votre-serveur)
6. [Vérification de la mise en place des recommandations de l'ANSSI](#6-vérification-de-la-mise-en-place-des-recommandations-de-lanssi-pour-sécuriser-notre-serveur-windows2025-document-1)
   - 6.1. [Vérifier la synchronisation horaire](#61-vérifier-la-synchronisation-horaire)
   - 6.2. [Vérifier que les fonctionnalités de sécurité natives sont activées](#62-vérifier-que-les-fonctionnalités-de-sécurité-natives-sont-activées)
   - 6.3. [Mettre à jour le serveur](#63-mettre-à-jour-le-serveur)
   - 6.4. [Sécuriser le compte « Administrateur local » du serveur Windows](#64-sécuriser-le-compte--administrateur-local--du-serveur-windows)

---

## Situation

Cette première situation consiste à réaliser les paramètres initiaux du prototype informatique. L'objectif est d'installer et de configurer un serveur Windows Server Core destiné à héberger ultérieurement le service Active Directory.

L'utilisation de Windows Server Core permet de renforcer la sécurité du système grâce à l'absence d'interface graphique et à la réduction des services et composants installés, limitant ainsi la surface d'attaque.

À l'issue de cette étape, le serveur Windows Server 2025 Core devra être installé, configuré, testé et validé conformément au cahier des charges et aux recommandations de l'ANSSI.

Vous devez enfin créer, dans l'environnement de virtualisation, une nouvelle machine virtuelle Windows Server 2025 Core sans utiliser de modèle prédéfini. Cette machine virtuelle portera le nom AD0 (étudiant 1) ou AD1 (étudiant 2) et fera l'objet des premiers paramétrages système et réseau.

## 1. Créer une VM à partir des indications ci-après :

**Virtual Machine 20501 (BLOC2-AdminSys-AD1) on node 'pve2'**

| Paramètre | Valeur |
|---|---|
| Memory | 4.00 GiB |
| Processors | 1 (1 sockets, 1 cores) [x86-64-v2-AES] |
| BIOS | OVMF (UEFI) |
| Display | Default |
| Machine | pc-q35-11.0+pve2 |
| SCSI Controller | VirtIO SCSI single |
| Hard Disk (ide0) | zfs-1:vm-20501-disk-1,size=32G |
| CD/DVD Drive (ide1) | local-data:iso/fr-fr_windows_server_2025_x64_dvd_bd6be507.iso,media=cdrom,size=5887386K |
| CD/DVD Drive (ide2) | local-data:iso/virtio-win-0.1.285.iso,media=cdrom,size=771138K |
| Network Device (net0) | e1000=BC:24:11:D3:F1:6D,bridge=ProjetB,firewall=1 |
| EFI Disk | zfs-1:vm-20501-disk-0,efitype=4m,ms-cert=2023k,pre-enrolled-keys=1,size=1M |
| TPM State | zfs-1:vm-20501-disk-2,size=4M,version=2.0 |

## 2. Vérifier la configuration IP de votre VM. Quel est votre constat ? :

Le DHCP est activé, le serveur tente donc d'obtenir une IP d'un serveur DHCP sans succès ce qui lui donne une adresse APIPA (169.254.243.58/16).

```
PS C:\Users\Administrateur> ipconfig /all

Configuration IP de Windows

   Nom de l'hôte . . . . . . . . . . : WIN-QJ5H8KPD597
   Suffixe DNS principal . . . . . . :
   Type de noeud. . . . . . . . . . . : Hybride
   Routage IP activé . . . . . . . . : Non
   Proxy WINS activé . . . . . . . . : Non

Carte Ethernet Ethernet :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) PRO/1000 MT Network Connection
   Adresse physique . . . . . . . . . . . : BC-24-11-D3-F1-6D
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::f5d9:4194:9393:3007%1(préféré)
   Adresse d'autoconfiguration IPv4 . . . : 169.254.243.58(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.0.0
   Passerelle par défaut. . . . . . . . . :
   IAID DHCPv6 . . . . . . . . . . . . . : 112993297
   DUID de client DHCPv6. . . . . . . . . : 00-01-00-01-32-29-F9-33-BC-24-11-D3-F1-6D
   Serveurs DNS. . . . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                             fec0:0:0:ffff::2%1
                                             fec0:0:0:ffff::3%1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
PS C:\Users\Administrateur>
```

## 3. Installer les drivers permettant la détection de votre carte réseau en utilisant les commandes PS suivantes :

```
PS C:\Users\Administrateur> Get-Volume

DriveLetter FriendlyName            FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining      Size
----------- ------------            -------------- --------- ------------ ----------------- -------------      ----
D           virtio-win-0.1.285      Unknown        CD-ROM    Healthy      OK                     0 B  753.06 MB
E           SSS_X64FRE_FR-FR_DV9    Unknown        CD-ROM    Healthy      OK                     0 B    5.61 GB
                                     FAT32          Fixed     Healthy      OK               62.78 MB     96 MB
C                                    NTFS           Fixed     Healthy      OK               23.88 GB  31.21 GB
                                     NTFS           Fixed     Healthy      OK              145.42 MB    688 MB

PS C:\Users\Administrateur> Start-Process D:\virtio-win-guest-tools.exe
PS C:\Users\Administrateur>
```

Utiliser **pnputil** dans le cas où vous ne parvenez pas à installer les drivers automatiquement.

```
PS C:\Users\Administrateur> Set-Service -Name "QEMU-GA" -StartupType Automatic
PS C:\Users\Administrateur> Start-Service QEMU-GA
```

## 4. Vérifier la détection de votre carte réseau et réaliser les paramétrages suivants :

```
PS C:\Users\Administrateur> Get-NetAdapter

Name          InterfaceDescription                     ifIndex Status    MacAddress          LinkSpeed
----          --------------------                     ------- ------    -----------          ---------
Ethernet      Intel(R) PRO/1000 MT Network Connection   6       Up        BC-24-11-D3-F1-6D    1 Gbps

PS C:\Users\Administrateur>
================================================================================
                            Paramètres de carte réseau
================================================================================

 Index NIC :             6
 Nom :                   Ethernet
 Description :           Intel(R) PRO/1000 MT Network Connection
 Adresse IP :            172.16.52.2,
                         fe80::f5d9:4194:9393:3007
 Masque de sous-réseau : 255.255.255.0
 DHCP activé :           False

 Passerelle par défaut : 172.16.52.254
 1er serveur DNS :       8.8.8.8
 2e serveur DNS :
 3e serveur DNS :

  1) Définir l'adresse de la carte réseau
  2) Définir les serveurs DNS
  3) Effacer les paramètres du serveur DNS
  4) Renommer la carte réseau

 Entrez la sélection (Vide = annuler):
```

## 5. Changer le nom de votre serveur :

```
================================================================================
                    Bienvenue dans Windows Server 2025 Standard
================================================================================

  1)  Domaine ou groupe de travail :         Groupe de travail : WORKGROUP
  2)  Nom de l'ordinateur :                  SERVEURAD1
  3)  Ajouter l'administrateur local
  4)  Gestion à distance :                   Activé

  5)  Paramètre de mise à jour :             Téléchargez uniquement
  6)  Installer les mises à jour
  7)  Bureau à distance :                    Désactivé

  8)  Paramètres réseau
  9)  Date et heure
  10) Paramètre des données de diagnostic : Nécessaire
  11) Activation de Windows

  12) Fermer la session utilisateur
  13) Redémarrer le serveur
  14) Arrêter le serveur
  15) Quitter vers la ligne de commande (PowerShell)

Entrez un nombre pour sélectionner une option: 2

================================================================================
                              Nom de l'ordinateur
================================================================================

Nom de l'ordinateur actuel : SERVEURAD1

Entrer un nouveau nom d'ordinateur (Vide = annuler): SERVEURAD1
```

## 6. Vérification de la mise en place des recommandations de l'ANSSI pour sécuriser notre serveur Windows2025 (Document 1) :

### 6.1. Vérifier la synchronisation horaire :

#### 6.1.1. Vérifier si un serveur de temps « NTP » est actuellement utilisé par votre serveur Windows :

#### 6.1.2. Modifier le serveur de temps pour prendre en compte les suivants : « 0.fr.pool.ntp.org 1.fr.pool.ntp.org » et forcer une première synchronisation :

```
PS C:\Users\Administrateur> w32tm /config /manualpeerlist:"0.fr.pool.ntp.org 1.fr.pool.ntp.org" /syncfromflags:manual /reliable:yes /update
La commande s'est terminée correctement.
PS C:\Users\Administrateur> w32tm /query /status
Indicateur de dérive : 0(Aucun avertissement)
Couche : 3 (Référence secondaire, synchronisée par (S)NTP)
Précision : -23 (119.209ns par battement)
Délai de racine : 0.0359817s
Dispersion de racine : 7.7639427s
ID de référence : 0x5243E814 (IP de la source :  82.67.232.20)
Heure de la dernière synchronisation réussie : 09/09/2026 10:47:11
Source : 0.fr.pool.ntp.org
Intervalle d'interrogation : 6 (64s)

PS C:\Users\Administrateur>
```

Vous pouvez aussi faire **w32tm /query /configuration** et vérifier NtpServer afin de savoir si la commande a bien était effectuée.

### 6.2. Vérifier que les fonctionnalités de sécurité natives sont activées :

#### 6.2.1. Vérifier l'activation de l'UAC :

EnableLUA doit être à un 1 pour être activé.

```
PS C:\Users\Administrateur> Get-ItemProperty 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\'

ConsentPromptBehaviorAdmin           : 5
ConsentPromptBehaviorEnhancedAdmin   : 2
ConsentPromptBehaviorUser            : 3
DelayedDesktopSwitchTimeout          : 0
DisableAutomaticRestartSignOn        : 1
DSCAutomationHostEnabled             : 2
EnableInstallerDetection             : 1
EnableLUA                            : 1
EnableSecureUIAPaths                 : 1
EnableUIADesktopToggle               : 0
EnableVirtualization                 : 1
EnterpriseDeviceAuthOnly             : 1
PromptOnSecureDesktop                : 1
TypeOfAdminApprovalMode              : 1
ValidateAdminCodeSignatures          : 0
disablecad                           : 0
dontdisplaylastusername              :
legalnoticecaption                   :
legalnoticetext                      :
scforceoption                        : 0
shutdownwithoutlogon                 : 0
undockwithoutlogon                   : 1
PSPath                               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\
                                        CurrentVersion\Policies\System\
PSParentPath                         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\
                                        CurrentVersion\Policies
PSChildName                          : System
```

Ajouter `-Name enableLua` pour obtenir plus d'informations sur la valeur du processus en question.

#### 6.2.2. Vérifier l'activation du pare-feu Windows Defender :

```
PS C:\Users\Administrateur> Get-NetFirewallProfile | Format-Table Name, Enabled

Name     Enabled
----     -------
Domain     True
Private    True
Public     True

PS C:\Users\Administrateur>
```

### 6.3. Mettre à jour le serveur :

#### 6.3.1. Installer le module « WindowsUpdate » pour les mises à jour :

```
PS C:\Users\Administrateur> Install-Module PSWindowsUpdate
```

#### 6.3.2. Vérifier les mises à jour disponibles :

```
PS C:\Users\Administrateur> Get-WindowsUpdate
```

#### 6.3.3. Installer les mises à jour proposées :

```
PS C:\Users\Administrateur> Install-WindowsUpdate
```

### 6.4. Sécuriser le compte « Administrateur local » du serveur Windows :

#### 6.4.1. Vérifier le SID (Security Identifier) du compte « Administrateur local » actuel :

```
PS C:\Users\Administrateur> Get-WmiObject -Class win32_UserAccount | Format-Table Name,SID

Name                  SID
----                  ---
Administrateur        S-1-5-21-334820341-3943162791-3466849576-500
DefaultAccount        S-1-5-21-334820341-3943162791-3466849576-503
Invité                S-1-5-21-334820341-3943162791-3466849576-501
WDAGUtilityAccount    S-1-5-21-334820341-3943162791-3466849576-504

PS C:\Users\Administrateur>
```

#### 6.4.2. Renommer le compte « Administrateur » en « ADM-SRV-00 » pour le serveurAD0 et vérifier si son SID est modifié :

```
PS C:\Users\Administrateur> Rename-LocalUser -Name "Administrateur" -NewName "ADM-SRV-01"
PS C:\Users\Administrateur> Get-WmiObject -Class win32_UserAccount | Format-Table Name,SID

Name                  SID
----                  ---
ADM-SRV-01            S-1-5-21-334820341-3943162791-3466849576-500
DefaultAccount        S-1-5-21-334820341-3943162791-3466849576-503
Invité                S-1-5-21-334820341-3943162791-3466849576-501
WDAGUtilityAccount    S-1-5-21-334820341-3943162791-3466849576-504

PS C:\Users\Administrateur>
```

Le SID est immuable, il ne changera jamais.

#### 6.4.3. Modifier le mot de passe « etudiant_007 » par un mot de passe qui respecte les recommandations de l'ANSSI : « BTS-SIO-cub-007-ANSSI-securite-admin » :

```
PS C:\Users\Administrateur> Set-LocalUser -Name ADM-SRV-01 -Password (Get-Credential).password

applet de commande Get-Credential à la position 1 du pipeline de la commande
Fournissez des valeurs pour les paramètres suivants :
Credential
```

Une fenêtre d'authentification s'ouvre alors, demandant le nom d'utilisateur (**ADM-SRV-01**) et le nouveau mot de passe à définir.
