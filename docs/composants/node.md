---
sidebar_position: 4
---

# Node

Il est possible d'ajouter des ressouces de calcul dans un cluster kubernets en faisant rejoindre des instances au sein de celui-ci. C'est l'instance qui s'enregiste sur le cluster.
Pour rejoindre un cluster une instance, qui sera appelée `node`, doit héberger certains éléments ainsi que connaitre l'url de l'api du cluster, le token et le certificat.
Les éléments qui doivent être présents sur la node pour fonctionner sont : un CRI/CRE pour executer des containers, le kubelet pour interragir avec l'api du cluster et le moteur de containeurs. Il faudra aussi le kube-proxy pour la partie overlay réseau. Quand une node s'enregistre sur un cluster la resource `Node` correspondante est créée et permet au cluster de suivre les évenements sur cette node. Une node doit être unique au sein d'un cluster, kubernetes s'appuie donc sur l'hostname de l'instance pour définir son nom.

## Container runtime

Chaque node peut avoir un container runtime différent même si cela n'est pas conseillé. Sur chaque node ce runtime fonctionnera de manière indépendant, c'est pour cela que des opérations comme récupérer les logs devra être réalisé sur chaque node.

## Kubelet

C'est l'interface entre l'api du cluster et le runtime pour les containeurs au travers d'un `shim` qui va transformer les requêtes grpc en opérations pour containeur comme on pourrait les réaliser avec un client comme `ctr`.

## Kube-proxy

Le kube-proxy doit fonctionner sur chaques nodes pour former l'overlay network qui permet de former un network simplifié pour l'interraction entre les pods, les services et les nodes.
