---
sidebar_position: 2
---

# Rappels

Kubernetes expose une api pour les éléments du cluster ainsi que pour interagir avec le client kubectl.

Il est possible d'accéder à cette api depuis son client grace à un proxy.

```shell
kubectl proxy # associe un port disponible en commencant par 8000
```
ou
```shell
#utiliser cette commande pour la suite
kubectl proxy --port=8080
```

Cela vous permettra d'accèder à l'api avec le path suivant `http://localhost:8080/api/`

## Curl API

Nous allons réaliser les commandes suivantes avec curl pour illuster que le client kubectl comme les composants du cluster, notamment les controlleurs, peuvent accéder aux ressources de l'api (à condition d'avoir les droits cf : roles/service account).

```shell
# Executer la commande suivante
curl http://localhost:8080/api/v1/namespaces/default
```

Le résultat présente le type de ressource, ca version et les metadatas et données (spec) ainsi que le status.

Namespace est un ressource standard de Kubernetes, mais il est possible de créer des ressources qui seront gérées par Kubernetes comme ces propres ressources.

## Ressources

```shell
# Executer les commandes suivantes
curl http://localhost:8080/apis/metrics.k8s.io
curl http://localhost:8080/apis/metrics.k8s.io/v1beta1
curl http://localhost:8080/apis/metrics.k8s.io/v1beta1/nodes
```

Les resources sont accessibles par l'ensemble des composants du cluster sous cette forme : `/apis/<api group>/<resource version>/<resource>`

On peut donc manipuler les objets kubernetes dans du code, et créer notre propre controller qui pourra surveiller/créer/supprimer des ressources dans notre cluster.

## Api resources

```shell
kubectl api-resource
```

Cette commande permet de lister les resources que le cluster peut gérer, aussi bien les ressources standards que les Custom Resource Definition (CRD).

![kube-api-structure](/img/kube-api-structure.png)
