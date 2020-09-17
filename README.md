# wikimedia

This is basic demo running wikimedia inside kubernetes in one pod.

## Insights

- use helm3

- wikimedia is packaged as single container with apache+php+sqlite database.

- I have sqlite db and LocalSettings.php files inside the same repository under [config](./config)

- I fetch sqlite db config tar, wikimedia tar and LocalSettings.php file using initContainer.

## Helm install

```
helm repo add wikimedia https://shivpathak.github.io/wikimedia/
helm repo update
helm search repo wiki
helm install demo wikimedia/helm-chart-wikimedia
```

After installation follow the screen to port-forward and access it over http://localhost:8080


## Credentials

**username:** wikimedia

**password:** wikimedia@123


**Note:** Not all features might be available as all php extensions are not installed in container:)


## Helm uninstall

```
helm uninstall demo
```

## Helm chart

Click on [helm-chart](./helm-chart-sources/helm-chart-wikimedia)