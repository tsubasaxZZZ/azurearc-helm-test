## Create

```console
export RESOURCE_GROUP=rg-aks-tsunomur0617
export CLUSTER_NAME=aks-tsunomur0617

az k8sconfiguration create \
--name azure-voting-app \
--resource-group  $RESOURCE_GROUP \
--cluster-name $CLUSTER_NAME \
--operator-instance-name azure-voting-app \
--operator-namespace prod \
--enable-helm-operator \
--helm-operator-version='0.6.0' \
--helm-operator-params='--set helm.versions=v3' \
--repository-url https://github.com/tsubasaxZZZ/azurearc-helm-test \
--operator-params='--git-readonly --git-path=releases/prod --git-poll-interval=1m --sync-garbage-collection' \
--scope namespace \
--cluster-type connectedClusters
```

## List
```console
az k8sconfiguration list --resource-group $RESOURCE_GROUP --cluster-name $CLUSTER_NAME   --cluster-type connectedClusters -o json
```

## Delete

```console
az k8sconfiguration delete  --resource-group $RESOURCE_GROUP --cluster-name $CLUSTER_NAME   --cluster-type connectedClusters --name azure-voting-app
```