# Kubernetes

## ¿Qué es Kubernetes?
***


## Arquitectura
***
El siguiente diagrama muestra la arquitectura de un cluster de Kubernetes

![](./resources/images/k8sGeneralArchitecture.png)

Un cluster de Kubernetes se divide en 2 componentes principales
* Master: Monitoriza los nodos
* Workers: Son los encargados de alojar los con


## Objetos de Kubernetes

### Pod
***
Es una instancia de una aplicación, es el objeto más pequeño que podemos crear en Kubernetes


#### Definición

```yaml
apiVersion: v1
kind: Pod
metadata: 
  name: my-pod
  labels:
    app: my-app
    
spec:
  containers:
    - name: nginx-container
      image: nginx

```

### Replication Controller
***
Es el objeto encargado de la alta disponibilidad

#### Definición

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: my-rc

spec:
  template:
    metadata:
      name: my-pod
      labels:
        app: my-app
    spec:
      containers:
      - name: nginx-container
        image: nginx

  replicas: 3
```

### Replica Set
***
Es el objeto encargado de la alta disponibilidad

#### Definición

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-rs

spec:
  template:
    metadata:
      name: my-pod
      labels:
        app: my-app
    spec:
      containers:
        - name: nginx-container
          image: nginx

  replicas: 3
  selector:
    matchLabels:
      app: my-app
```

### Deployment
***
Es el objeto encargado de la alta disponibilidad

Rollout: cuando se lanza un deployment se crea una revisión de lo nuevo y antiguo




```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment

spec:
  template:
    metadata:
      name: my-pod
      labels:
        app: my-app
    spec:
      containers:
        - name: nginx-container
          image: nginx

  replicas: 3
  selector:
    matchLabels:
      app: my-app
```

## Comandos
***

#### Crear un recurso
```shell
kubectl apply -f mainfest.yml
```

```shell
kubectl create -f mainfest.yml
```

```shell
kubectl replace -f mainfest.yml
```

```shell
kubectl scale --replicas=6 -f mainfest.yml
```

```shell
kubectl delete -f mainfest.yml
```

## Bibliografía
***
[Documentación Oficial](https://kubernetes.io/es/docs/home/)