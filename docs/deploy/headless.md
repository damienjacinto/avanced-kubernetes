---
sidebar_position: 3
---

# Headless

Dasn kubernetes il y a plusieurs type de service pour exposer un pod :

- Loadbalancer
- ClusterIP
- NodePort
- Headless

Un service permet de répartir du flux entre plusieurs pods sélectionner (selector).

## Loadbalancer

Il sert à déclarer un loadbalancer au près du clouder qui aura comme backend le service, cela permet d'exposer publiquement un service de manière robuste (fonctionnalités avanbcées du loadbalancer du clouder). Le service aura comme ip l'ip du loadbalancer.

## ClusterIP

Permet d'exposer un ensemble de pod en interne du cluster ou pour un ingress, c'est le service par défaut.

## NodePort

Un service NodePort utilise un port de la node pour exposer de manière publique un service, ce n'est pas très robuste car on expose directement la node.

## Headless

Pour activer le mode headless d'un service, son type doit être `ClusterIP` et le champ clusterIp égal à `None` qui represente l'ip virtuelle du service. Le service n'ayant pas d'ip c'est l'ip des pods qui est directement exposé. Ce mode est beaucoup utilisé pour exposer des applications `StatefulSet` cela permet au client de s'enregistrer sur l'ip du pod et réutiliser cette ip pour les prochaines interrogations. Les pods statefull ayant un état différent entre les réplicas cela peut être interressant de présenter à un utilisateur le même pod pour qu'il retoruve ces données.
