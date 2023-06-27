---
sidebar_position: 2
---

# Ingress Controller

Afin d'exposer du flux depuis l'extérieur sans service mesh, l'utilisation d'un ingress controller avec un service de type loadbalancer est la manière recommendée.
La resolution dns de votre site va pointer vers le loadbalancer de votre clouder, le backend du loadbalancer sera le service de l'ingress contoller qui controllera l'aiguillage du flux par les ingress vers les services ClusterIP de vos microservices.

![ingress](/img/ingress.jpg)
