# Objectif du Repository

L'objectif de ce repository est d'automatiser l'installation de **Jenkins**, **SonarQube**, **Nexus** et **Artifactory** à l'aide de leurs images Docker, le tout via **Ansible**.

---

## Prérequis

- Un navigateur
- Une connexion internet

### Windows :
- Avoir **WSL2** installé sur la machine pour utiliser le terminal Ubuntu afin d'effectuer ce travail.

---

## Étapes d'installation

### 1. Mise à jour des paquets

Dans votre terminal, exécutez les commandes suivantes :

```bash
sudo apt update
sudo apt upgrade
```
### 2. Installation d'Ansible

```sudo apt install ansible -y```

### 3. Installation de Docker via Ansible

Il existe un playbook appelé installer_docker.yml. Lancez-le avec la commande suivante : ```ansible-playbook installer_docker.yml --ask-become```
Après avoir lancé cette commande, vous serez invité à entrer votre mot de passe root. Appuyez ensuite sur Entrée.

### 4. Vérification de l'installation de Docker

Pour vérifier que Docker est correctement installé, exécutez la commande suivante : ```docker run hello-world```

### 5. Installation des images Docker des outils

Lancez le playbook installer_outils_devops.yml avec la commande suivante : ```ansible-playbook installer_outils_devops.yml --ask-become```

### 6.Verification de l'installation des images

Après l'exécution complète du playbook, vérifiez les images téléchargées avec la commande : ```docker images```

### 7.Création des containers avec les images téléchargées

Lancez le playbook creer_containers_tests.yml avec la commande suivante : ```ansible-playbook creer_containers_tests.yml --ask-become```

### 8. Vérification de la création des containers
     ####Pour Windows :
      1. Avant tout, vous devrez connaître l'adresse IP privée de votre WSL2. Pour ce faire, exécutez : ip a ; Prenez l'IP sous eth0 (##par exemple, 172.19.8.220/20).
      2. Récupérez cette adresse IP et ouvrez votre navigateur (pensez à vider votre cache).
      3.Pour afficher l'interface Jenkins par défaut, entrez l'URL suivante dans votre navigateur : 172.19.8.220:8080
      4.Pour afficher l'interface Sonarqube par défaut, entrez l'URL suivante dans votre navigateur : 172.19.8.220:9000
      5.Pour afficher l'interface Nexus par défaut, entrez l'URL suivante dans votre navigateur : 172.19.8.220:8081
      6.Pour afficher l'interface Artifactory par défaut, entrez l'URL suivante dans votre navigateur : 172.19.8.220:5000
     ####Pour les autres OS, il vous suffit de consulter votre navigateur et cibler les ports spécifiés. N'oubliez pas de vider le cache de votre navigateur.
> 9. Nettoyage après vérification
  Une fois que vous avez vérifié que tout fonctionne parfaitement, retournez dans votre terminal, appuyez sur Entrée pour continuer le playbook, puis les containers de test seront   supprimés automatiquement





