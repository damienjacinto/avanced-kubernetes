---
sidebar_position: 3
---

# Control plane

Element principal du cluster, expose l'api qui sera utilisé pour interragir avec le cluster. Il est composé de plusieurs éléments qui sont tous prévus pour fonctionner de manière distribuée.
Les élements du control plane peuvent être installé sur la même instance qui peut servir de node dans le cluster. Pour les charges de travail en production on préferera avoir le control plane en HA (mini 3 instances). Les éléments du cluster échangent de facon sécurisé par SSL. Il est possible d'utiliser le même certificat pour tous les éléments mais pour la production on va préférer utiliser des certificats différents.

## kube-apiserver

L'api du cluster, de préférence cette api doit être privée. C'est l'élément névralgique du cluster et le point d'entrée pour administrer le cluster.

## etcd

Base de données clé-valeur qui conserve les ressources et leurs états. L'ensemble des instances d'etcd sont renseignés dans les paramètres d'etcd pour le quorum mais aussi dans l'api de kubernetes pour la haute disponibilité.

## kube-scheduler

Controlleur en charge de placer les pods sur les nodes en fonction de son algorithme et son paramétrage. On peut avoir plusieurs scheduleur dans le même cluster avec une priorité.

## kube-controller-manager

Controlleur principal du cluster qui gère les ressources standards (nodes, endpoints, etc)

## static pod

Il est possible de déployer des pods dans le cluster sans passer par l'api. En effet un paramètre permet de spécifier un dossier qui sera chargé avec le démarrage du cluster. Les manifestes des pods placés dans ce dossier seront démarrés avec le cluster, leur nom est suffixé du nom de la node. C'est souvent la manière d'installer des composants en mode "bootstrap" comme etcd ou le kube proxy au sein d'un cluster.
