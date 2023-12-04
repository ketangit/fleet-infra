## fleet-infra

### First steps
```shell 
# install flux-cli, create repo, and GitHub PAT

export GITHUB_TOKEN=<YOUR-PAT>
export GITHUB_USER=ketangit

flux check --pre

flux bootstrap --version=v2.1.2 github --owner=${GITHUB_USER} --repository=fleet-infra --branch=main --personal --components-extra image-reflector-controller,image-automation-controller
```

### Install dashboard
```shell
# install gitops-cli

export PASSWORD=<SUPER-SECRET-PASSOWRD>

gitops create dashboard ww-gitops --password=${PASSWORD} --export > ./clusters/my-cluster/weave-gitops-dashboard.yaml

```

### Images required
```console
ghcr.io/fluxcd/helm-controller:v0.36.2
ghcr.io/fluxcd/kustomize-controller:v1.1.1
ghcr.io/fluxcd/notification-controller:v1.1.0
ghcr.io/fluxcd/source-controller:v1.1.2
ghcr.io/fluxcd/image-automation-controller:v0.36.1
ghcr.io/fluxcd/image-reflector-controller:v0.30.0


export GITHUB_TOKEN=<YOUR-PAT>
export GHCR_TOKEN=$(echo $GITHUB_TOKEN | base64)

curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/helm-controller/tags/list
curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/kustomize-controller/tags/list
curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/notification-controller/tags/list
curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/source-controller/tags/list
curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/image-automation-controller/tags/list
curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/image-reflector-controller/tags/list

curl -H "Authorization: Bearer $GHCR_TOKEN" https://ghcr.io/v2/weaveworks/charts/weave-gitops/tags/list
```
