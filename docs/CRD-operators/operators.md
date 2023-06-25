---
sidebar_position: 4
---

# Operators

L'opérateur est la brique logicielle qui va observer les changements sur une ou plusieurs CRD pour appliquer des modifications au sein du clusteur ou sur des ressources extérieures. Il est composé d'un ou plusieurs controlleurs qui fonctionnent selon le même pattern d'observation que les controlleurs standards de kubernetes.

## Fonctionnement

![crd](/img/operator.png)

## Controlleurs

Les controlleurs sont généralement développés en go car kubernetes étant développé dans ce langage il existe de nombreuses librairies et framework pour développer ces propres controlleurs et interragir avec l'api du cluster.
Le contolleur sera installé dans le cluster comme une application standard avec un service, un deploiement et un pod. Le deploiement sera généralement opéré par helm.

:::caution

Il faudra donner assez de droits au service account du controlleur pour manipuler les objects standards et les CRD (clusterrole) tout en respectant le principe de "least privilege".

:::

## Catalogue

https://operatorhub.io/
