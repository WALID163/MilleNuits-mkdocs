-----

# SP2 – Mission 1 : Création d’une documentation avec MkDocs et GitHub Pages

**Auteur :** Walid
**Projet :** Mille nuits

-----

## Table des matières 

1.  [Installation MkDocs et le thème Material](https://www.google.com/search?q=%231--installation-mkdocs-et-le-th%C3%A8me-material)
2.  [Créer son nouveau projet](https://www.google.com/search?q=%232---cr%C3%A9er-son-nouveau-projet)
3.  [Hébergement sur Github pages](https://www.google.com/search?q=%233---h%C3%A9bergement-sur-github-pages)
4.  [Utilisation d'un éditeur pour le markdown](https://www.google.com/search?q=%234---utilisation-dun-%C3%A9diteur-pour-le-markdown)

-----

## 1 - Installation MkDocs et le thème Material

### Prérequis

  * Python 3.8 ou + (pour avoir accès à la commande pip) 
  * Git (pour le git bash et les commandes) 

### Installation

Dans l'invite de commande, exécutez les commandes suivantes pour installer MkDocs et le thème Material :

```bash
pip install mkdocs 
pip install mkdocs-material
```

Une fois l'installation terminée, vous pouvez vérifier la version avec :

```bash
mkdocs --version 
```

-----

## 2 - Créer son nouveau projet

Nous allons créer un répertoire entièrement géré par un fichier de configuration nommé `mkdocs.yml`. 

### Commandes de création

```bash
mkdocs new millenuits 
cd millenuits
```

### Structure du projet

La commande génère la structure suivante :

  * `millenuits/` 
      * docs/` 
          * index.md` 
      * `mkdocs.yml`

### Configuration du fichier `mkdocs.yml` 

Le fichier `.yml` permet de modifier le nom du site, le thème ou la navigation : 

```yaml
site_name: Mille Nuits 
theme:
  name: material 

nav:
  - Home: index.md 
  - Doc: crys.md 
```

-----

## 3 - Hébergement sur Github pages 

### Configuration sur GitHub

1.  Créer un nouveau repository sur GitHub.
2.  Définir la visibilité sur **Public**. 
3.  Envoyer (Push) les fichiers du projet MkDocs (via Git ou GitHub Desktop). 

Commandes Git : 

```bash
git init 
git add . 
git commit -m "Initial commit" 
git remote add origin https://github.com/utilisateurs/nomdurepo
git branch -M main 
git push -u origin main 
```

### Activation de GitHub Pages 

  * Rendez-vous dans **Settings** → **Pages**. 
  * Activez les **GitHub Actions**. 
  * Créez un fichier de workflow dans `.github/workflows/deploy.yml` pour automatiser le "build" et le déploiement à chaque changement. 

**Exemple de script de déploiement :** 

```yaml
name: Deploy MkDocs (gh-deploy) 

on:
  push:
    branches:
      - main 

permissions:
  contents: write 

jobs:
  deploy:
    runs-on: ubuntu-latest 
    steps:
      - uses: actions/checkout@v4 
      - uses: actions/setup-python@v5 
        with:
          python-version: 3.x 
      - name: Install MkDocs
        run: pip install mkdocs mkdocs-material 
      - name: Deploy
        run: mkdocs gh-deploy --force 
```

-----

## 4 - Utilisation d'un éditeur pour le markdown 

Il est nécessaire d'utiliser un éditeur pour rédiger vos fichiers Markdown. 
Dans ce guide, nous utilisons **Obsidian**. 

  * Installation : Télécharger Obsidian sur internet. 
  * Utilisation : Vous pouvez ouvrir votre dossier de projet (le repo) en tant que "coffre" (vault) pour éditer directement vos fichiers `.md`. 
-----
