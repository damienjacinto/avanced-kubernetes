---
sidebar_position: 2
---

# Stateful vs Deployment

Kubernetes fonctionne plus efficacement avec des applications stateless et la ressource `Deployment`.
Il est possible cependant d'utiliser la ressource `StatefulSet` pour des applications stateful.

Ces deux ressources permettent d'utiliser des volumes pour utiliser du stockage physique mais la principal différence aura lieu lors du scaling.
Chaque pod issu d'un `Statefulset` va utiliser son propre volume indépendant contrairement à un deploiement stateless qui vont partager le meme volume.

Une autre particularité des pods issus d'un `Statefulset` est qu'ils vont conserver une identité (nommage) fixe avec une séquence, contrairement à un `Deployment` où les noms des pods sont suffixés par l'id du ReplicaSet et d'un id unique pour le pod.

```ssh
k get pods

NAME                        READY   STATUS  RESTARTS    AGE
deployment-75675f5897-8qc9o	1/1	    Running	0           25s
deployment-75675f5897-kzcij	1/1	    Running	0           25s
deployment-75675f5897-qsznm	1/1	    Running	0           25s

k get pods

NAME        READY   STATUS  RESTARTS    AGE
stateful-0  1/1     Running	0	        47
stateful-1  1/1	    Running	0	        38s
stateful-2  1/1	    Running	0	        21s
```
