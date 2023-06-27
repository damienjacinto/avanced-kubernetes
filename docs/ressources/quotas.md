---
sidebar_position: 2
---

# Quotas

Les administrateurs d'un cluster peuvent définir des quotas par namespace pour limiter les ressources disponibles.
Il est possible de définir des quotas sur les ressources standard CPU/memory mais aussi sur des métriques custom ou même un nombre de ressources.

## Exemple

```
apiVersion: v1
kind: ResourceQuota
metadata:
  name: limit-pods
spec:
  hard:
    cpu: "1000"
    memory: 200Gi
    pods: "1"
    services: "1"
```

:::info
Si un quota existe avec des limites en cpu ou memory, il faudra définir des requests sur les pods.
:::

