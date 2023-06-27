---
sidebar_position: 1
---

# Quality of service - QoS

Kubernetes utilise par défaut un niveau de qualité sur les pods en fonction des informations présentes.

![qos](/img/qos.png)

Ce niveau de qualité définit quels pods seront éjectés en premier si une node manque de ressources.

Guaranteed > Burstable >  Best Effort

Il est possible de définir d'autres priorityclasses avec des scores supérieurs.

Une éviction de pod est lancée lorsque les ressources physiques disponibles sur une node dépasse le threshold défini sur le kubelet (config)

[node-pressure](https://kubernetes.io/docs/concepts/scheduling-eviction/node-pressure-eviction/)
