# Bienvenue chez Adimeo !

Le process d'installation de ta nouvelle machine pose comme prérequis l'installation d'une distribution Linux Ubuntu LTS (18.04 actuellement).

## Mise à jour

Avant de continuer, mets à jour ton système :

```
sudo apt update
sudo apt dist-upgrade
```

La première ligne ira récupérer les mises à jour des logiciels installés en fonction des dépôts (repositories) configurés dans `/etc/apt/sources.list` et `/etc/apt/sources.list.d/*`.

La seconde ligne, quant à elle, installera ces mises à jour pour les logiciels et installera toute nouvelle dépendance le cas échéant.

## Installation d'Ansible

Afin d'installer les outils et logiciels nécessaires au démarrage du développement nous allons utiliser l'outil Ansible. Pour cela il te faut l'installer :

> :warning: **Exécute bien ces prochaines lignes. Cela te permettra d'installer la dernière version d'Ansible. Sinon toutes ses fonctionnalités ne seraient pas présentes...**

```
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install -y ansible ssh sshpass
```

Enfin tape cette commande afin d'autoriser une connexion SSH à ta propre machine : 

```
ssh-keyscan -H 127.0.0.1 >> ~/.ssh/known_hosts
```

Ça y est ? Prêt à lancer la bête ?

## Récupération du script d'installation

Ansible va s'occuper à jouer des tâches qui, l'une après l'autre, installeront des outils et logiciels sur ta machine. Le script est disponible à cette adresse : [ansible-dev-machine](https://github.com/adimeo-lab/ansible-dev-machine/releases).

Une fois téléchargé et décompressé, va dans le dossier avec le terminal. En supposant que ce dossier est décompressé dans ton dossier `Documents` :


```
cd ~/Documents/ansible-dev-machine
```

## Exécution des tâches

Tu peux exécuter les tâches : 

```
ansible-playbook \
  -i hosts playbook.yml \
  --extra-vars "ansible_user=__USER__ ansible_password=__PASSWORD__ email_username=__EMAIL_USERNAME_ ansible_become_password=dqhgz51"
```

Pense à remplacer dans cette commande les valeurs suivantes :

* `__USER__` : ton nom d'utilisateur ;
* `__PASSWORD__` : ton mot de passe.
* `__EMAIL_USERNAME_` : ton nom d'utilisateur en rapport avec ton email. Exemple, si ton email est `jdoe@adimeo.com`, la valeur de `__EMAIL_USERNAME_` devra être `jdoe`

Une fois lancer, n'hésite pas à aller boire un café, ça va prendre du temps !

## Explication de ce qui a été installé

### Les logiciels de base

* **curl**
  * transfert de paquets via des urls
* **vim**
  * éditeur de fichier en ligne de commande
* **nano**
  * éditeur de fichier en ligne de commande (c'est pour ceux qui ne savent pas utiliser vim :D)
* **git**
  * gestion de code
* **screen**
  * multiplexeur de terminaux
* **gcc**
  * compilateur C
* **make**
  * constructeur d'outils sur base de Makefile
* **wget**
  * outil permettant le téléchargement de ressources sur un réseau
* **ssh**
  * client SSH
* **snapd** & **snapd-xdg-open**
  * outils pour intéragir avec les snaps
* **software-properties-common**
  * permet une gestion simple des sources logicielles
* **php**
  * installation de plusieurs versions de PHP
* **phpstorm**
  * IDE de développement PHP
* **virtualbox**
  * Outil de virtualisation
* **Google Chrome**
  * Navigateur internet
* **visual studio code**
  * éditeur de code (JavaScript, Frontend, ...)
* **Docker**
  * outil de conteneurisation
* **NodeJS**
  * JavaScript coté serveur
* **ZSH**
  * terminal

### PhpStorm

TODO

### Microsoft Visual Studio Code

TODO

### Screen

TODO

### Vim

TODO

### Zsh

TODO

### Git

TODO

### PHP

TODO


