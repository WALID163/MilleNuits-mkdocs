# Mission 1 - Maquettage de l'infrastructure réseau

**Boisseau Crys — 801 — 06/11/2025**  
*Lycée Paul-Louis Courier — Le lycée de tous les parcours*

---

## Table des matières

- [A. Zone, Équipements, Ports et IP](#a-zone-équipements-ports-et-ip)
- [B. Test de connexions](#b-test-de-connexions)

---

## A. Zone, Équipements, Ports et IP

### Ferme de serveurs — VLAN 53 : `172.16.53.0/24`

| Équipement | IP | Port sur Switch |
|---|---|---|
| Switch-SERVEUR | — | Cuivre Fa7/1, Fa8/1, Fa9/1 ; Fibre Gig6/1 |
| Serveur WEBFTPSIO | 172.16.53.1/24 | Cuivre Fa9/1 |
| Serveur TICKETSIO | 172.16.53.2/24 | Cuivre Fa8/1 |
| Serveur NASSIO | 172.16.53.3/24 | Cuivre Fa7/1 |

### Routeur

| Port | Adresse IP |
|---|---|
| Fibre Gig9/0 | 172.16.53.253 |
| Fibre Gig8/0 | 172.16.29.14 |

### Les différents services réseau : `172.16.29.0/22`

| Équipement | IP | Port |
|---|---|---|
| Switch-DEV | — | Cuivre Fa9/1 ; Fibre Gig8/1 |
| Poste DEV01 | 172.16.29.1/22 | Fibre Gig8/1 |

---

## B. Test de connexions

### Test services Web

Depuis le poste **DEV01**, accès à l'URL `http://172.16.53.1` via le navigateur Web :

> La page Cisco Packet Tracer s'affiche correctement — connexion au serveur **WEBFTPSIO** réussie.

---

### Test service FTP

Depuis **DEV01**, connexion FTP au serveur `172.16.53.1` :

```
C:\>ftp 172.16.53.1
Trying to connect...172.16.53.1
Connected to 172.16.53.1
220- Welcome to PT Ftp server
Username: cisco
331- Username ok, need password
Password:
230- Logged in
(passive mode On)
ftp>
```

> Connexion FTP au serveur **WEBFTPSIO** réussie.

---

### Test des connexions réseau entre les équipements

#### Ping passerelle du réseau 172.16.29.0

```
C:\>ping 172.16.29.13

Pinging 172.16.29.13 with 32 bytes of data:

Reply from 172.16.29.13: bytes=32 time<1ms TTL=255
Reply from 172.16.29.13: bytes=32 time<1ms TTL=255
Reply from 172.16.29.13: bytes=32 time<1ms TTL=255
Reply from 172.16.29.13: bytes=32 time<1ms TTL=255

Ping statistics for 172.16.29.13:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

#### Ping Serveur WEBFTPSIO

```
C:\>ping 172.16.53.1

Pinging 172.16.53.1 with 32 bytes of data:

Reply from 172.16.53.1: bytes=32 time<1ms TTL=127
Reply from 172.16.53.1: bytes=32 time<1ms TTL=127
Reply from 172.16.53.1: bytes=32 time<1ms TTL=127
Reply from 172.16.53.1: bytes=32 time<1ms TTL=127

Ping statistics for 172.16.53.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

#### Ping Serveur TICKETSIO

```
C:\>ping 172.16.53.2

Pinging 172.16.53.2 with 32 bytes of data:

Reply from 172.16.53.2: bytes=32 time<1ms TTL=127
Reply from 172.16.53.2: bytes=32 time<1ms TTL=127
Reply from 172.16.53.2: bytes=32 time<1ms TTL=127
Reply from 172.16.53.2: bytes=32 time<1ms TTL=127

Ping statistics for 172.16.53.2:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

#### Ping Serveur NASSIO

```
C:\>ping 172.16.53.3

Pinging 172.16.53.3 with 32 bytes of data:

Reply from 172.16.53.3: bytes=32 time<1ms TTL=127
Reply from 172.16.53.3: bytes=32 time<1ms TTL=127
Reply from 172.16.53.3: bytes=32 time<1ms TTL=127
Reply from 172.16.53.3: bytes=32 time<1ms TTL=127

Ping statistics for 172.16.53.3:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

#### Ping passerelle par défaut réseau 172.16.53.0

```
C:\>ping 172.16.53.253

Pinging 172.16.53.253 with 32 bytes of data:

Reply from 172.16.53.253: bytes=32 time<1ms TTL=255
Reply from 172.16.53.253: bytes=32 time<1ms TTL=255
Reply from 172.16.53.253: bytes=32 time=2ms TTL=255
Reply from 172.16.53.253: bytes=32 time<1ms TTL=255

Ping statistics for 172.16.53.253:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 2ms, Average = 0ms
```
