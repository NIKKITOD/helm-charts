# Simple Chart Repo
## Prerequisites
---
Make sure you have Helm installed.

## Get Repo Info
---
```
helm repo add nikitod https://nikkitod.github.io/helm-charts
helm repo update
```
See ```helm repo``` for command documentation.

## Deploy App to your cluster
---
### Deploy Stack
```
helm install 
```
### Deploy Backend only 
```
helm install <release-name> nikitod/backend -n <release-namespace>
```
### Deploy Frontend only 
```
helm install <release-name> nikitod/frontend -n <release-namespace>
```
### Deploy with custom values
Use ```--set```
```
helm install foo-bar nikitod/app-stack --set backend.image.repository=foo/bar
```
or ```--values``` file
```
helm install foo-bar nikitod/app-stack --values foo-bar.yml
```
## Configure custom values
---
Default _Backend_ values list
```
appVersion:

common:                 # base config
  include_nginx: False  # enable/disable nginx 
  ports:                # list of ports for app deployment/service
    - name: http
      port: 80

image:                  # docker image config
  registry: docker.io   
  repository:
  tag: latest

volume:                 # volume config
  enabled: false        # enable/disable volume
  persistStorage:
    static:
      size:
  storageClass:

config:                 # list of values for app configmap
   - name:
    value:

secrets:                # list of values for app secrets
  - name:
    value:
```
Default _Frontend_ values list
```
appVersion:

common:                 # base config
  ports:                # list of ports for add deplyment/service
    - name: http
      port: 3000

image:                  # docker image config
  registry: docker.io
  repository:
  tag: latest

config:                 # list of values for app configmap
  - name:
    value:

secrets:                # list of values for app secrets
  - name:
    value:
```
---
_slepnevns@gmail.com_