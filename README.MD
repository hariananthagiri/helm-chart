# HELM CHART
* templatise the kubernetes manifests
* package manager for kubernetes
* to parameterise the values used in manifest.yaml we use helm sheet

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
* to see the history how many times we deployed in helm use below command
```
helm history <app-name>
```
* to do the rollback in helm use below command
```
helm rollback <app-name>
```
* to goto particular revision in helm use below command
```
helm history relese revision
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
* we can set the values.yaml file values at command line by using below command
```
--set key=value
<command> --set deployment.replicas=10
helm upgrade nginx --set deployment.replicas=10
```
* to see all the volues stored in volues.yaml file use below command
```
helm show values . 
```
* we have install ebs drivers to our helm folder as below in VM
```
helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver
helm repo update
helm upgrade --install aws-ebs-csi-driver --namespace kube-system aws-ebs-csi-driver/aws-ebs-csi-driver
helm list -n kube-system
```
* to uninstall the driver use below command
```
helm uninstall aws-ebs-csi-driver -n kube-system
```
#### Statefulset
* it is used to create stateful applications in kubernetes
* podes inside stateful applications should have static hostnames to communicate with other nodes
* stateful applications should follow orderly provisioning as well as terminaete 
* statefulset applications will have headless service.
* it definetly requied PV or PVC
* **deployment**  
    * it is used to create stateless (i.e no own database) applications in kubernetes


