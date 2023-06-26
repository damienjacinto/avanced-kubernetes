---
sidebar_position: 2
---

# Exercices suite

## Node shutdown

- Arreter l'instance node1 sans stoper la node coté kubernetes (Non-graceful node shutdown)
- Relancer l'instance

## ETCD

- Installer etcd-client pour interragir avec etcd
- Définir la version de l'api avant de manipuler etcdctl `export ETCDCTL_API=3`
- Lister les endpoints présents pour etcd et identifier les valeurs pour les certificats
- Lister les membres du cluster etcd
```ssh
sudo ETCDCTL_API=3 etcdctl --endpoints $ENDPOINTS --cacert $CACERT --cert $CERT --key $KEY member list
```
- Ajouter un clé à etcd
```ssh
sudo ETCDCTL_API=3 etcdctl --endpoints $ENDPOINTS --cacert $CACERT --cert $CERT --key $KEY put foo bar
```
- Watch clé foo depuis le master
```ssh
sudo ETCDCTL_API=3 etcdctl --endpoints $ENDPOINTS --cacert $CACERT --cert $CERT --key $KEY watch foo
```
- Changer la valeur de foo depuis une autre session pour illustrer comment les controlleurs sont notifiés dans changemnet sur les ressources.

## ETCD backup/restore

[etcd](https://etcd.io/docs/v3.3/op-guide/recovery/)

- Deployer un pod dans le cluster
- Faire un backup de etcd
- Detruire le pod
- Restaurer etcd en spécifiant un nouveau répertoire pour les données (on ne pas faire un restore "in-place")
- Mettre à jour les informations pour etcd pour utiliser le nouveau répertoire (--data-dir)
- Lister les pods du cluster
