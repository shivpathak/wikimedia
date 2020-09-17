# wikimedia

This is basic demo running wikimedia inside kubernetes in one pod.

Requirement:

- use helm3
- wikimedia is apacked as single container with apache+php+sqlite database.


Steps to install wiki media in kubernetes:

```
helm repo add wikimedia https://shivpathak.github.io/wikimedia/
helm repo update
helm search repo wiki
helm install demo wikimedia/helm-chart-wikimedia
```

Access wikimedia on http://localhost:8080 using kubectl port forwarding

```
export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=helm-chart-wikimedia,app.kubernetes.io/instance=demo" -o jsonpath="{.items[0].metadata.name}")
kubectl --namespace default port-forward $POD_NAME 8080:80
```

**Note:** Not all features might be available as all php extensions are not installed in container:)

_To login to wikimedia use following credential_

**username** wikimedia
**password** wikimedia@123