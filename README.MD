# HELM CHART
* templatise the kubernetes manifests
* package manager for kubernetes

* **INSTALLATION**
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
### Helm Commands
* to install anything in helm chart we use below command


* the first step is helm chart is Chart.yaml as shown in below
```yaml
apiVersion: v1
name: nginx
version: 0.0.2 # this the chart version
description: this is the customised helm chart for nginx
appVersion: 1.0.1
```
