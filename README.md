# Bienvenue chez Adimeo !

Le process d'installation de ta nouvelle machine pose comme prérequis l'installation d'une distribution Linux Ubuntu LTS (18.04 ou 20.04).

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
sudo apt-add-repository --yes --update ppa:ansible/ansible # only on Ubuntu <= 18.04
sudo apt install -y ansible ssh sshpass
```

Enfin tape cette commande afin d'autoriser une connexion SSH à ta propre machine : 

```
mkdir -p ~/.ssh && ssh-keyscan -H 127.0.0.1 >> ~/.ssh/known_hosts
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
  --extra-vars "lsb_release=__RELEASE__ ansible_user=__USER__ ansible_password=__PASSWORD__ email_username=__EMAIL_USERNAME_ ansible_become_password=__PASSWORD__"
```

Pense à remplacer dans cette commande les valeurs suivantes :

* `__RELEASE__` : ta release Ubuntu (focal pour 20.04, bionic pour 18.04) ;
* `__USER__` : ton nom d'utilisateur ;
* `__PASSWORD__` : ton mot de passe.
* `__EMAIL_USERNAME_` : ton nom d'utilisateur en rapport avec ton email. Exemple, si ton email est `jdoe@adimeo.com`, la valeur de `__EMAIL_USERNAME_` devra être `jdoe`

Une fois lancer, n'hésite pas à aller boire un café, ça va prendre du temps !

