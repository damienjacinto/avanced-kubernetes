---
sidebar_position: 3
---

# CRD

On peut étendre les possibilités d'un cluster en créant des nouveaux types de ressources appelés Custom Resources Definiton (CRD), les CRD sont une ressource comme les autres.

Il est possible de les consulter, les créer, les supprimer.

```shell
kubectl get crd
```

La définition de notre resource ainsi que les resources créées seront persistées dans ETCD. Avant de pouvoir "instancier" notre resource il faudra appliquer la définition du CRD. Cette opération est souvent réalisée en amont de l'installation de l'opérateur qui va gérer vos nouvelles ressources, soit directement par une url appliquée avec kubectl soit par une chart helm. Un concensus semble émerger sur l'utilsiation d'une chart juste pour les CRD et une chart pour l'opérateur et de les lier par dépendance.

:::caution

Supprimer la défintion d'un CRD entraine la suppression des instances de ces ressources car kubernetes ne sait plus les gérer. Attention aux effets de suppression en cascade

:::

## Définition

Un CRD étant une resource kubernetes il est possible de décrire la définition de la resource en YAML. La définition suit les mêmes règles que les ressources standards (apigroup, kind, name, ect).

### Exemple:

```yaml
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  name: killoldpod.example.com
spec:
  group: example.com
  versions:
    - name: v1
      served: true
      storage: true
      schema:
        openAPIV3Schema:
          type: object
          properties:
            spec:
              type: object
              properties:
                minutes:
                  type: integer
                  minimum: 1
                namespace:
                  type: string
                  minLength: 1
  scope: Namespaced
  names:
    plural: killoldpods
    singular: killoldpod
    kind: KillOldPod
    shortNames:
    - kop
```

:::note

- Installer ce CRD comme exemple dans un cluster pour la suite.
- Créer une ressource de type KillOldPod dans le namespace default qui va cibler les pods du namespace testoperator et qui stoppera les pods vieux de plus de 5 min.

:::

### Group

Premet de regrouper les resources crées sous un meme nom (scope) pour les futures accès. Il est préconisé de construire ce nom de groupe sous la forme `<project name>.<company domain>.<extension>` avec un domaine possédé par le créateur de la resource pour éviter les collisions en effet les CRD ne sont pas limité à un namespace.

### Versions

Il est important de versionner ses ressources pour prévoir des futures changements non rétroactivement compatible (breaking change)

### Détails

Dans un crd on va décrire comment l'api va exposer et donc comment kubectl va pouvoir accéder aux resources. On peut définir des alias, si la resource créée sera "scope" namespace par exemple.
On peut définir aussi les champs affichés lors d'un GET, définir les champs obligatoires, des valeurs par défaut, des validations pour les valeurs, ect.

![crd](/img/crd-to-instance-map.jpg)

### Documentation

https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#validation-rules

https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#defaulting

https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#additional-printer-columns
