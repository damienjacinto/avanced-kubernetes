---
sidebar_position: 1
---

# Ingress

Cette ressource agit comme un routeur de flux exterieur vers les services de types ClusterIP. Il est possible de faire du routing en fonction de l'hote , du path et leur combinaison.

L'ingress permet aussi de réaliser la terminaison SSL avant de transmettre le flux à un service.
Un ingress fonctionne avec un ingress controller, il est possible d'utiliser plusieurs ingress controllers par la valeur de `className`.

:::info
Certain ingress controller utilise leur propre ressource, certain comme Traefik permettent d'utiliser les ingress standard ou leur ressources.
:::
