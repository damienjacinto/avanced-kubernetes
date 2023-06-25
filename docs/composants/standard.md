---
sidebar_position: 2
---

# Open Standard

Kubernetes est maintenant un produit mature organisé autour de standards. Ces standards définissent des interfaces/apis/spécifications permettant à différents produits interchangeables de remplir leur rôle au sein d'un cluster.

## Open Container Initiative - OCI

Cet organisme gère les spécifications en lien avec la conteneurisation. [OCI](https://opencontainers.org/)

### Image Specification

La défintion de standards concernant les images des conteneurs a permis de définir les manifests, index, layers qui constituent aujourd'hui les containeurs que l'on manipule.
Cela nous permet de construire nos images avec d'autres outils que docker comme podman, kaniko qui offrent des solutions rootless.

Ces standards permettent aujourd'hui aux registries respectant la spécification d'héberger des charts helm en plus des images.

[Image Specification](https://github.com/opencontainers/image-spec/blob/main/spec.md#overview)

### Runtime Specification Abstract

Kubernetes a déprecié docker au profit de CRI qui implémentent les dernieres versions de cette spécification. La plus part des alternatives s'appuient sur `runC`.
[Runtime Specification](https://github.com/opencontainers/runtime-spec/blob/main/spec.md)

![cri-shim](/img/cri-shim.png)

## Container Runtime Interface - CRI

Implémentation de l'interface discutant avec le kubelet permettant de lancer les containers sur une node. Le kubelet discute avec l'interface en grpc avec le parametre `--image-service-endpoint`.

### Produits

Docker, contairned, CRI-O

## Container Network Interface - CNI

Plugin permettant de gérer la partie network sur les nodes. Un ou plusieurs CIDR sont définis pour constituer le réseau virtuel privé dans lequel l'adressage de kubernetes aura lieu.
La correspondance entre l'ip du réseau kubernetes et la vraie ip est gérée différement suivant la solution. Certaine solution comme Calica utilise la table d'ip, certaine solution comme Cilium utilise ebpf (modules kernels)

![cni](/img/cni.png)

### Produits

Calico, Flannel, Cilium, WeaveNet

## Container Storage Interface - CSI

Plugin permettant à kubernetes d'interragir avec le system de stockage physique. Les resources kubernetes comme `StorageClass` sont interprétés par le plugin pour être transmis à la couche qui gère le stockage.

[Container Storage Interface](https://github.com/container-storage-interface/spec/blob/master/spec.md)

![csi](/img/csi.png)

### Produits

Rook, Ceph, OpenEBS
