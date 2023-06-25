---
sidebar_position: 1
---

# Introduction

L'évolution de kubernetes semble tendre à se recentrer sur son noyau de fonctionnalités et laisser à la communauté le soin d'étendre kubernetes. C'est le rôle principal des Custom Definiton Resource (CRD) et des opérateurs.

Il existe deux principales raisons d'étendre le fonctionnement de kubernetes :

- La première est de personnaliser la fonctionnement de kubernetes, par exemple pendant très longtemps les CronJobs ne géraient pas les timezones, la communauté a donc créé des alternatives pour gérer ce cas précis.

- La seconde est la volonté de gérer des outils supplémentaires au sein d'un cluster kubernetes. L'exemple le plus parlant est les bases de donées. Il existe aujourd'hui des opérateurs pour gérer une base de données PostgreSQL au sein de votre cluster. Des projets comme Crossplane utilise les fonctionnalités d'un cluster kubernetes pour gérer des resources cloud extérieur au cluster.

Il existe d'autres raisons, mais elles se rejoignent dans l'idée d'utiliser un seul outil `kubernetes` et de l'étendre pour combler les besoins. Cela permet de conserver les mêmes méthodes, process et bonne pratiques au dela des resources standards.
