# Preparation

```shell
export CI=1
export CLIENT_ID=e1406013-b316-4f84-8ca2-a3e43fc97853
export CLIENT_SECRET=LuedS7Wa08~DAb2t2mCq7BacdFkF_.kGls
export TENANT_ID=cb3030c5-477e-430d-bd98-8d67a79c4ac0
export AZURE_SUBSCRIPTION_ID=6c140a2a-c627-4756-85b1-ca26dba4c07c
```

## Reuse the same storage account created for the backend
```shell
ng add @azure/ng-deploy --resource-group catfacts --account catfacts1604
```

## Reuse the same storage account created for the backend
## enable static website hosting
## Don't forget to change the account name with the one you used previously
```shell
az storage blob service-properties update --account-name catfacts1604 --static-website --404-document index.html --index-document index.html
```

## Fix CORS issue (origin url=output of deployment)
```shell
az functionapp cors add --name catfacts1604-api --resource-group catfacts --allowed-origins https://catfacts1604.z1.web.core.windows.net
```

# Deployment
```shell
ng deploy
```
