# Kubernetes

- kubectl

---

> kubectl get a shell to the running container

```
$ kubectl exec -it -n staging <podNameWithHas> -- /bin/bash
```

> kubectl get env

```

\$ kubectl exec -it -n staging <podNameWithHas> env

```

> helm delete pod

```

\$ helm delete <podNameWithoutHas> --purge

```

> apply secret

1. create file testFolder/staging.yaml

   <b>Note: projectName sendit-k8s-secret</b>

```

apiVersion: v1
kind: Secret
metadata:
    name: group-namme
type: Opaque
data:
    password1:YWRtaW4=

```

2. create screate by contexts(staging, development, production)

<b>Note: swith contexts from Kubernetic before run command</b>

```

kubectl apply -n production -f testFolder/production.yaml
kubectl apply -n development -f testFolder/development.yaml
kubectl apply -n staging -f testFolder/staging.yaml

```

> create ingress

<b>Note: swith contexts from Kubernetic before run command projecName sendit-infra-cluste/helm-ingress</b>

- /values-frontend-staging.yaml for frontend

script path = scripts

```

helm upgrade -i ingress-frontend-staging helm-ingress -f helm-ingress/values-frontend-staging.yaml --namespace=stagin

```

- /values-api-staging.yaml for backend

script path = scripts

```
$ helm upgrade -i ingress-api-staging helm-ingress  -f helm-ingress/values-api-staging.yaml --namespace=staging
```

> use local server instand of stagng server

- install telepresence
- start project
- run telepresence command in terminal

```
> telepresence --namespace staging --swap-deployment <deployment-service-name>
```

> generate vpn kube

1. go to [git-lab](https://gitlab.com/sendit-th) search ovpn-k8s
2. clone project and open project ovpn-k8s in vscode
3. follow process in README.MD
   - open docker
   - open gen-ovpn.sh
   - change CLIENTNAME to your name
   - run ./gen-ovpn.sh in terminal
   - pass phrase is "senditdev" without quote
