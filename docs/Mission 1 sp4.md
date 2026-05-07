# SP4 - Mission 1 : Mise en place d’unenvironnement de test conteneurisé

**BOISSEAU Crys-801**

---
## 1. Installation de Docker et Docker Compose
  Avant toute installation, mettez à jour votre machine Linux (Debian ou Ubuntu):
```bash
sudo apt update && sudo apt upgrade -y
```
  Installez ensuite les paquets nécessaires:
```bash
sudo apt-get install docker
sudo apt-get install docker-compose
```

### Vérification du fonctionnement
  Vérifiez les versions installées pour confirmer le succès de l'opération:
*  **Docker Compose** : `docker-compose --version` 
*  **Docker** : `docker --version`

  Pour tester le moteur, lancez un conteneur simple:
```bash
sudo docker run hello-world
```

---

## 2. Interface Web Portainer
  Portainer permet de gérer vos conteneurs via une interface graphique.

1.    **Création du répertoire** : `sudo mkdir -p /root/docker/portainer`.
2.    **Configuration** : Créez un fichier `docker-compose.yml` avec la configuration suivante:
    *   **Image** : `portainer/portainer-ce:latest` 
    *   **Ports** : `9000:9000` 
    *   **Volumes** : Liaison du socket Docker et persistance des données via `portainer_data`.
3.    **Lancement** : `docker-compose up -d`.
4.    **Accès** : `http://ip-du-serveur-docker:9000`.

---

## 3. Services Web et Base de Données
### Service Web (Apache/PHP)
*   **Répertoire** : `/home/etudiant/docker/html`.
*   **Image** : `php:8.2-apache`.
*   **Configuration** : Port `8080:80` et volume lié au dossier `./site`.
*   **Dépendance** : Le service attend que la base de données (`db`) soit prête.

### Base de données (MySQL)
*   **Répertoire** : `/home/etudiant/docker/mysql`.
*   **Image** : `mysql:8`.
* **Variables d'environnement** :
    *   `MYSQL_ROOT_PASSWORD`: root 
    *   `MYSQL_DATABASE`: monsite 
*   **Test de connexion**:
    ```bash
    sudo docker exec -it mysql_db mysql -uAdmMysql -p
    ```

---

## 4. Versionning avec GitHub
### Initialisation
  Installez Git et configurez votre identité:
```bash
sudo apt install git
git config --global user.name "Boisseau"
git config --global user.email "crys.boisseau@gmail.com"
```
  Initialisez le dépôt dans votre dossier `docker/` avec `git init`.

### Sécurité (.gitignore)
  Créez un fichier `.gitignore` pour exclure les données sensibles et inutiles:
*   `docker-data/`
*   `*.log`
*   `.env`
*   Répertoires d'IDE (`.vscode/`, `.idea/`)

### Publication sur GitHub
  Après avoir créé un répertoire sur GitHub, exécutez:
1.    `git add .` (Ajouter les fichiers) 
2.    `git commit -m "Initialisation du projet"`
3.    `git remote add origin [URL_DU_DEPOT]`
4.    `git push -u origin main`

>   **Note** : Pour le mot de passe lors du push, utilisez un **token** généré sur GitHub.
