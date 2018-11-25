## Exercice

Dans cet exercice, vous allez créer un Pod et l'exposer à l'extérieur du cluster en utilisant un Service de type **NodePort**.

### 1. Création d'un Pod

Créez un fichier *www_pod.yaml* définissant un Pod ayant les propriétés suivantes:
- nom: **www**
- label associé au Pod: **app: www** (ce label est à spécifier dans les metadatas du Pod)
- nom du container: **nginx**
- image du container: **nginx:1.12.2**

### 2. Lancement du Pod

La commande suivante permet de créer le Pod

```
$ kubectl create -f www_pod.yaml
```

### 3. Définition d'un service de type NodePort

Créez un fichier *www_service_NodePort.yaml* définissant un service ayant les caractéristiques suivantes:
- nom: **www-np**
- type: **NodePort**
- un selector permettant le groupement des Pods ayant le label **app: www**.
- forward des requètes vers le port **80** des Pods sous-jacents
- exposition du port **80** dans le cluster
- exposition du port **31000** sur le cluster

### 4. Lancement du Service

A l'aide de **kubectl** créez le Service défini dans *www_service_NodePort.yaml*

### 5. Accès au Service depuis l'extérieur

Lancez un navigateur sur le port 31000 de l'une des machines du cluster.

Si vous utilisez **minikube**, vous n'avez qu'un seul node et l'URL sera de la forme **http://192.168.99.100:31000**

![Service NodePort](./images/service_NodePort.png)
