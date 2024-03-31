# capten-plugins

Project to adminster capten plugin content

## plugin-store

Configure Capten plguin applications

Sample Plugin application configuration

```
pluginName: "my-app"
description: "Sample plugin app"
category: "CI/CD"
icon: "app.svg"
pluginConfig:
  apiEndpoint: https://myapp.{{.DomainName}}/api
  uiEndpoint: https://myapp.{{.DomainName}}/ui
  uiModulePackageURL: https://myapp.{{.DomainName}}/ui-package/my-app.zip
  capabilities:
    - deploy-controlplane-cluster
    - deploy-bussiness-cluster
    - capten-sdk
    - ui-sso-oauth
    - postgress-store
    - vault-store
deploymentConfig:
  controlplaneCluster:
    chartName: "my-app-chart1"
    chartRepo: "https://kube-tarian.github.io/helmrepo-supporting-tools"
    versions:
        - "v1.0.2"
    defaultNamespace: "my-app1"
    privilegedNamespace: false
  bussinessCluster:
    chartName: "my-app-chart2"
    chartRepo: "https://kube-tarian.github.io/helmrepo-supporting-tools"
    versions:
        - "v1.0.5"
    defaultNamespace: "my-app2"
    privilegedNamespace: false
```
