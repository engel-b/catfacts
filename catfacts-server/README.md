# Preparation
## Create service principal
```shell
az ad sp create-for-rbac -n sls-principal
```

>{
  "appId": "e1406013-b316-4f84-8ca2-a3e43fc97853",
  "displayName": "sls-principal",
  "name": "http://sls-principal",
  "password": "LuedS7Wa08~DAb2t2mCq7BacdFkF_.kGls",
  "tenant": "cb3030c5-477e-430d-bd98-8d67a79c4ac0"
}

## Create a new resource group
```shell
az group create --name catfacts --location germanywestcentral
```

## Create the storage account
## This name must be globally unique, so change it with your own
```shell
az storage account create --name catfacts1604 --resource-group catfacts --kind StorageV2
```

## Create the function app
## This name must be globally unique, so change it with your own
```shell
az functionapp create --name catfacts1604-api --resource-group catfacts --consumption-plan-location germanywestcentral --storage-account catfacts1604 --functions-version 3 --runtime node --runtime-version 14
```

# Deployment
## Build your app
```shell
npm run build
```

## Clean up node_modules to keep only production dependencies
```shell
npm prune --production
```

## Create an archive from your local files and publish it
## Don't forget to change the name with the one you used previously
```shell
func azure functionapp publish catfacts1604-api
```
