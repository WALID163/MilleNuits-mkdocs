# SP4 - Mission 1 - fiche recette - Docker

### Informations Générales
* **BOISSEAU Crys-801**
* **Objet** : Fiche de recette pour la mise en œuvre de la solution.
* **Statut global** : Reçu (Validé).

---

### Tests de Connectivité et Résultats

| Description du test | Résultats Attendus | Commentaire / Observation |
| :--- | :--- | :--- |
| **Accès depuis le réseau Dev** : Un PC sur le réseau Dev tente de se connecter à un conteneur Docker et à Internet. | Le PC parvient à se connecter au conteneur, mais l'accès à Internet échoue. | Le test est concluant : la connexion au conteneur fonctionne alors que l'accès Internet est bloqué, conformément aux attentes. |
| **Restriction du serveur Docker** : Le serveur Docker tente de pinger Internet ainsi que des adresses IP hors du réseau Dev. | Échec de l'ensemble des tentatives de ping. | Le serveur Docker est restreint : il ne peut communiquer qu'avec les IP de son propre réseau et celles du réseau Dev. |

---

### Conclusion de la réception
* **Décision** : Le projet est marqué comme **Reçu**.
* **Note technique** : Le serveur Docker est configuré pour un isolement strict, limitant ses communications aux réseaux locaux autorisés (son propre réseau et le réseau Dev).
