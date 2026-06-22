# Testing web app with Azure Entra ID and Key Vault

Spring act as Application Client in terms of OAuth 2.0. 
This client ses Authorization Code Flow to authenticate users with Azure Entra ID and access Key Vault secrets.

Class that get the id_token and access_token after user successfully login with Azure Entra ID and 
authenticate the client.


**_`org.springframework.security.oauth2.client.web.OAuth2LoginAuthenticationFilter`_**


The id_token is used to get user information, while the access_token is used to access Key Vault secrets.

## Azure container testing MANUALLY

## azure_web_app_client_ad
Azure Cloud tesing

# Steps

## Install the AZURE CLI

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

## Login to AZURE CLI (AZ)

```bash
az login
```

## Login to ACR

```bash
az acr login -n [AZURE_REGISTRY_NAME]
```


## Tag teh docker image before pushing it to azure container registry
```bash
docker tag azure_web_app_demo:0.0.1 [REGISTRY_NAME]-[HASH_CREATED_BY_AZURE_ACR].azurecr.io/azure_web_app_demo:0.0.1

```


## Push the docker image to ACR
```bash
docker image push [AZURE_REGISTRY_NAME]-[HASH_CREATED_BY_AZURE_ACR].azurecr.io/azure_web_app_demo:0.0.1

```


## Need to login to other ACR, first logout from existing account

```bash
az acr logout
```

