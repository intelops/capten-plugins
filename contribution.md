# Contributing Guidelines

## Welcome to Capten-Plugin Contributing section 🎉

Hi there! We're thrilled that you'd like to contribute to this project, thank you for your interest. Whether it's a bug report, new feature, correction, or additional documentation, we greatly value feedback and contributions from our community.

Please read through this document before submitting any issues or pull requests to ensure we have all the necessary information to effectively respond to your bug report or contribution.

### Directory Structure 

The repository follows this structure:

```

capten-plugins/
├── .readme_assets/        # Assets for the README
├── plugin-store/          # Main directory for plugin configurations
│   ├── plugin-list.yaml   # List of plugins
│   └── <plugin-name>/     # Directory for each plugin
│       ├── icon.svg       # Plugin icon
│       ├── plugin-config.yaml # General plugin configuration
│       └── <version>/     # Directory for each version of the plugin
│           ├── plugin-config.yaml # Version-specific configuration
│           └── values.yaml        # Version-specific values
├── plugins/               # Additional plugin resources
├── README.md              # Repository overview
└── CONTRIBUTING.md        # Guidelines for contributing


```
## Steps to Contribute

### Additional Plugin Support


1. Add Plugin Application name

Add the plugin application name in `plugin-store/plugin-list.yaml` file

```
plugins:
  - argo-cd
  - crossplane
  - tekton
```


2. Add Plugin Application Configuration

Create a folder with plugin name `plugin-store/<plugin-name>`, and add plugin metadata files

- Add plugin application configuration in `plugin-store/<plugin-name>/plugin-config.yaml` file
- Add plugin application Icon file in `plugin-store/<plugin-name>/icon.svg`

| Attribute   | Description                           |
| ----------- | ------------------------------------- |
| pluginName  | Plugin application name               |
| description | Plugin application description        |
| category    | Plugin application category           |
| icon        | Plugin application icon               |
| versions    | Plugin application supported versions |


```
pluginName: "argo-cd"
description: "GitOps continuous delivery tool for Kubernetes"
category: "CI/CD"
icon: "icon.svg"
versions:
  - "v1.0.2"
  - "v1.0.5"
```

you can refer [here](https://github.com/intelops/capten-plugins/blob/main/plugin-store/argo-cd/plugin.yaml)

3. Add Plugin Application Version Deployment Configuration

For each supported version, create version folder `plugin-store/<plugin-name>/<version>` and add plugin version deployment metadata files

- add plugin application version deployment configuration in `plugin-store/<plugin-name>/<version>/plugin-config.yaml` file
- add plugin application version values file in `plugin-store/<plugin-name>/<version>/values.yaml` file

\*\* plugin application version deployment configuration attributes \*\*
| Attribute | Description |
| ------------------- | ---------------------------------------- |
| chartName | Plugin application chart name |
| chartRepo | Plugin application chart repo |
| version | Plugin application version |
| defaultNamespace | Plugin application default namespace |
| privilegedNamespace | Plugin application privileged namespace |
| valuesFile | Plugin application values file |
| apiEndpoint | Plugin application API endpoint |
| uiEndpoint | Plugin application ui endpoint |
| capabilities | Plugin application required capabilities |



Table below shows an example of plugin application version deployment configuration

| Capabilities                | Description                                                      |
| --------------------------- | ---------------------------------------------------------------- |
| deploy-controlplane-cluster | Capability to deploy plugin application on control plane cluster |
| deploy-bussiness-cluster    | Capability to deploy plugin application on business cluster      |
| capten-sdk                  | Capability to access Capten cluster SDK                          |
| ui-sso-oauth                | Capability to enable Single SignOn for plugin application UI     |
| postgress-store             | Capability to access Capten cluster storage service              |
| vault-store                 | Capability to access Capten cluster vault service                |

```
deployment:
  controlplaneCluster:
    chartName: "argo-cd"
    chartRepo: "https://kube-tarian.github.io/helmrepo-supporting-tools"
    version: "v1.0.2"
    defaultNamespace: "argo-cd"
    privilegedNamespace: false
    valuesFile: "values.yaml"
apiEndpoint: https://argo.{{.DomainName}}
uiEndpoint: https://argo.{{.DomainName}}
capabilities:
  - deploy-controlplane-cluster
  - capten-sdk
  - ui-sso-oauth
```

You can have sample reference of argocd plugin [here](https://github.com/intelops/capten-plugins/tree/main/plugin-store/argo-cd)