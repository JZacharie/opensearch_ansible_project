# Projet d'installation d'OpenSearch avec Ansible

## Description

Ce projet contient les fichiers Ansible nécessaires pour déployer un cluster OpenSearch de 3 nœuds sur des machines Ubuntu 20.04. 
Le cluster est configuré sans sécurité ni SSL pour simplifier le déploiement initial.

## Structure du projet
    opensearch_ansible_project/
    ├── playbook.yml
    ├── inventory.ini
    ├── opensearch.yml.j2
    └── jvm.options.j2

- `playbook.yml`: Le playbook Ansible principal qui orchestre l'installation et la configuration d'OpenSearch.
- `inventory.ini`: Le fichier d'inventaire qui liste les hôtes cibles pour le déploiement.
- `opensearch.yml.j2`: Un template Jinja2 pour la configuration d'OpenSearch.
- `jvm.options.j2`: Un template Jinja2 pour la configuration JVM d'OpenSearch.

## Prérequis

- Ansible 2.9 ou supérieur installé sur la machine de contrôle.
- Trois machines Ubuntu 20.04 avec un accès SSH pour le déploiement du cluster.
- Python 3.x installé sur les machines cibles.

## Configuration

1. Modifiez le fichier `inventory.ini` pour refléter les adresses IP et les informations de connexion de vos machines cibles.
2. Si nécessaire, ajustez les variables dans le fichier `playbook.yml`.

## Fonctionnalités

- Installation automatisée d'OpenSearch sur trois nœuds.
- Configuration d'un cluster multi-nœuds avec tous les nœuds en tant que maîtres potentiels.
- Installation de Java (OpenJDK 11) comme dépendance.
- Configuration dynamique de la mémoire heap basée sur la mémoire disponible de chaque machine.
- Désactivation de la sécurité et du SSL pour un déploiement simplifié (à ne pas utiliser en production).
- Vérification de la santé du cluster après le déploiement.

## Utilisation

1. Assurez-vous que vos machines cibles sont accessibles via SSH.
2. Exécutez le playbook avec la commande suivante :

```bash
ansible-playbook -i inventory.ini playbook.yml
```
