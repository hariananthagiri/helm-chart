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
```
helm install <app-name> .
```
* to see the list of all components we did with helm we use below command
```
helm list
```
* after changeing values to upgrade use below command
```
helm upgrade <app-name> .
```
1. Chart.yaml
    * the first step is helm chart is Chart.yaml as shown in below
```yaml
apiVersion: v1
name: nginx
version: 0.0.2 # this the chart version
description: this is the customised helm chart for nginx
appVersion: 1.0.1 # apk version
```
2. templates
    * we definately need to give a folder named templates in helm charts all deploymentand .yaml file are automatically executed here
3. values.yaml
    * we maintain values.yaml file in root folder to import and export values 
* we declere a variable as below
```
* for number use below syntax
{{ .Values.<section-name>.<variablename> }}
```
* for alpha numaric or text use below syntax
```
"{{ .Values.<section-name>.<variablename> }}"
```
* if we give quote there while passing the value in values.yaml there also we need to give quote
* **example**
```
"nginx:{{ .Values.deployment.imageVersion}}"
```
* in values.yaml ile we pass as below
```yaml
deployment:
  replicas: 3
  imageVersion: mainline-alpine3.18-perl
```