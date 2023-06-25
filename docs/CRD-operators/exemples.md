---
sidebar_position: 5
---

# Exemples

## Cert-manager Operator

Certainement le controlleur le plus connu, il permet de gérer les certificats, les challenges ainsi que leur renouvellement automatique. Il est souvent utilisé pour fournir des certificats `let's encrypt`.

## Prometheus stack

Element incontournable dans le monitoring sur kubernetes, il existe un operateur pour simplifier la configuration et la fédération des instances de prometheus et alertmanager. Les CRD permettent de définir les configurations qui seront injectés dans les instances de prometheus et alertmanager gérées par l'opérateur.

## Crossplane

Crossplane est un opérateur visant à mapper des ressources kubernetes avec des ressources externes notamment celles des clouders. Il se place comme une alternative au outil d'Iaac comme terraform. Le state est l'état de la ressource kubernetes et la boucle de réconcilliation sert à provisionner les ressources dans l'api distant. Il faut installer le provider ainsi que les
ressources que l'on veut gérer sous la forme de CRD qui est plus simple à gérer de manière gitops qu'un énorme fichier de configmaps.

## Postgres-operator

Contolleur permettant de déployer une base de données Postgres dans un cluster mais surtout de paramétrer les tâches administatives comme les backups ou les montées de version.
