---
sidebar_position: 1
---

# Exercices

Construire un cluster kubernetes avec 1 seul master et 2 nodes.

## Master

- Creer un user, son home, et lui donner les droits pour sudo pour continuer l'installaton sous ce user
- Désactiver le swap
- Installer containerd pour notre container runtime engine (package container.io)
- Creer une config par défaut pour containerd
- Activer Cgroup dans le configuration de containerd
- Install crictl pour avoir un client pour interragir avec containerd (sinon utiliser ctr)
- Definir la socket à utiliser en regardant les logs de containerd (crictl config runtime-endpoint `<<socket>>`)
- Redemarrer containerd et vérifier qu'il est possible de run un container comme nginx avec ctr ou critctl (docker.io/library/nginx:latest)
- Installer les outils pour bootstrap le cluster, kubelet, kubeadm, kubectl
- Utilsier kubeadm pour installer le cluster (sudo kubeadm init --pod-network-cidr=192.168.0.0/16 --cri-socket unix:///run/containerd/containerd.sock)
- Copier la configuration admin pour votre user, et noter la commande pour rejoindre le cluster
- Vérifier les processus, kubeadm a configuré pour nous :  etcd, kube-scheduler, kube-apiserver, kube-controller-manager. Identifier l'url de etcd et celle de l'api de kubernetes
- A ce stade on peut lister les nodes du cluster, Quel est l'état de la node master ?
- Installer callico (https://docs.tigera.io/calico/latest/getting-started/kubernetes/quickstart). Editer la resouce Installation si le cidr du cluster n'est pas 192.168.0.0/16
- Lister à nouveau les nodes une fois callico installé, vérifier les taints et labels
- Lister tous les pods du cluster et observer leur nom
- Réaliser la même opération avec crictl

## Nodes

- Ajouter deux nodes au cluster
- Installer les éléments indispensables (reprendre les mêmes produits que le master même si ce n'est pas obligatoire)
- Utiliser la commande pour join le cluster fourni par kubeadm
- Il faut récupérer une configuration pour kubectl

## Observations

- Ajouter un pod nginx dans le namespace `default` sans passer par l'api depuis le master
- Exposer le pod par un service avec kubectl
- Visualiser les routes sur le master

```ssh
sudo iptables -t nat -L PREROUTING | column -t
sudo iptables -t nat -L KUBE-SERVICES -n | column -t
```

