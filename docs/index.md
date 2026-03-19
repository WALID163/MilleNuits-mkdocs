Voici une transformation du document en format Markdown structuré, basée sur les informations fournies.

-----

# Mission 1 : Création d’une documentation avec MkDocs et GitHub Pages

[cite_start]**Auteur :** Walid JOUAL [cite: 1, 2]
[cite_start]**Projet :** Mille nuits [cite: 3]
[cite_start]**Classe :** 801 [cite: 4]

-----

## [cite_start]Table des matières [cite: 7, 9]

1.  [Installation MkDocs et le thème Material](https://www.google.com/search?q=%231--installation-mkdocs-et-le-th%C3%A8me-material)
2.  [Créer son nouveau projet](https://www.google.com/search?q=%232---cr%C3%A9er-son-nouveau-projet)
3.  [Hébergement sur Github pages](https://www.google.com/search?q=%233---h%C3%A9bergement-sur-github-pages)
4.  [Utilisation d'un éditeur pour le markdown](https://www.google.com/search?q=%234---utilisation-dun-%C3%A9diteur-pour-le-markdown)

-----

## [cite_start]1 - Installation MkDocs et le thème Material [cite: 10]

### Prérequis

  * [cite_start]Python 3.8 ou + (pour avoir accès à la commande pip) [cite: 11]
  * [cite_start]Git (pour le git bash et les commandes) [cite: 12]

### Installation

[cite_start]Dans l'invite de commande, exécutez les commandes suivantes pour installer MkDocs et le thème Material : [cite: 13]

```bash
[cite_start]pip install mkdocs [cite: 14, 19]
[cite_start]pip install mkdocs-material [cite: 15]
```

[cite_start]Une fois l'installation terminée, vous pouvez vérifier la version avec : [cite: 21]

```bash
[cite_start]mkdocs --version [cite: 22]
```

-----

## [cite_start]2 - Créer son nouveau projet [cite: 23]

[cite_start]Nous allons créer un répertoire entièrement géré par un fichier de configuration nommé `mkdocs.yml`. [cite: 24, 31]

### Commandes de création

```bash
[cite_start]mkdocs new millenuits [cite: 25]
[cite_start]cd millenuits [cite: 26]
```

### [cite_start]Structure du projet [cite: 27]

La commande génère la structure suivante :

  * [cite_start]`millenuits/` [cite: 28]
      * [cite_start]`docs/` [cite: 29]
          * [cite_start]`index.md` [cite: 30]
      * [cite_start]`mkdocs.yml` [cite: 31]

### [cite_start]Configuration du fichier `mkdocs.yml` [cite: 33]

[cite_start]Le fichier `.yml` permet de modifier le nom du site, le thème ou la navigation : [cite: 33]

```yaml
[cite_start]site_name: Mille Nuits [cite: 37]
theme:
  [cite_start]name: material [cite: 39, 41]

nav:
  - [cite_start]Home: index.md [cite: 43, 45]
  - [cite_start]Doc: crys.md [cite: 47]
```

-----

## [cite_start]3 - Hébergement sur Github pages [cite: 48]

### Configuration sur GitHub

1.  [cite_start]Créer un nouveau repository sur GitHub. [cite: 49, 50]
2.  [cite_start]Définir la visibilité sur **Public**. [cite: 53]
3.  [cite_start]Envoyer (Push) les fichiers du projet MkDocs (via Git ou GitHub Desktop). [cite: 54]

[cite_start]**Commandes Git :** [cite: 55]

```bash
[cite_start]git init [cite: 56]
[cite_start]git add . [cite: 57]
[cite_start]git commit -m "Initial commit" [cite: 58]
[cite_start]git remote add origin https://github.com/utilisateurs/nomdurepo [cite: 59]
[cite_start]git branch -M main [cite: 60]
[cite_start]git push -u origin main [cite: 61]
```

### [cite_start]Activation de GitHub Pages [cite: 63]

  * [cite_start]Rendez-vous dans **Settings** → **Pages**. [cite: 64]
  * [cite_start]Activez les **GitHub Actions**. [cite: 65]
  * [cite_start]Créez un fichier de workflow dans `.github/workflows/deploy.yml` pour automatiser le "build" et le déploiement à chaque changement. [cite: 66, 118]

[cite_start]**Exemple de script de déploiement :** [cite: 69, 72]

```yaml
[cite_start]name: Deploy MkDocs (gh-deploy) [cite: 72]

on:
  push:
    branches:
      - [cite_start]main [cite: 75, 77, 79, 81]

permissions:
  [cite_start]contents: write [cite: 89, 90]

jobs:
  deploy:
    [cite_start]runs-on: ubuntu-latest [cite: 91, 92, 93]
    steps:
      - [cite_start]uses: actions/checkout@v4 [cite: 101, 102]
      - [cite_start]uses: actions/setup-python@v5 [cite: 103]
        with:
          [cite_start]python-version: 3.x [cite: 104]
      - name: Install MkDocs
        [cite_start]run: pip install mkdocs mkdocs-material [cite: 112, 114]
      - name: Deploy
        [cite_start]run: mkdocs gh-deploy --force [cite: 115, 116]
```

-----

## [cite_start]4 - Utilisation d'un éditeur pour le markdown [cite: 125]

[cite_start]Il est nécessaire d'utiliser un éditeur pour rédiger vos fichiers Markdown. [cite: 126] [cite_start]Dans ce guide, nous utilisons **Obsidian**. [cite: 128]

  * [cite_start]**Installation :** Télécharger Obsidian sur internet. [cite: 129, 130]
  * [cite_start]**Utilisation :** Vous pouvez ouvrir votre dossier de projet (le repo) en tant que "coffre" (vault) pour éditer directement vos fichiers `.md`. [cite: 131, 135, 136]

-----

Souhaitez-vous que je vous aide à rédiger le contenu du fichier `index.md` pour votre projet ?
