# Azure/Docker Build and Deploy Commands

## Backend

```sh
docker build --secret id=django-private-key.txt,src="../secrets/django-private-key.txt" --secret id=mssql-username.txt,src="../secrets/mssql-username.txt" --secret id=mssql-password.txt,src="../secrets/mssql-password.txt" -t pottercontainerregistry.azurecr.io/invapp-backend:latest .
docker push pottercontainerregistry.azurecr.io/invapp-backend:latest
```

## Frontend

```sh
docker build -t pottercontainerregistry.azurecr.io/invapp-frontend:latest .
docker push pottercontainerregistry.azurecr.io/invapp-frontend:latest
```

## Azure Container Registry

```sh
az login
az acr login --name pottercontainerregistry
```

### Azure Portal Setup

#### Secret Volumes

- Container App -> Settings -> Secrets -> Configure All Secrets Needed
- Container App -> Revisions and replicas -> Volumes -> Add -> Secret/(name)/(Configure All Secrets Needed)
- Container App -> Revisions and replicas -> Create new revision -> Container -> Select Container -> Volume Mounts -> (Configure to mount secret volume)

#### Ingress/Networking

- Container App -> Settings -> Ingress -> Enabled/Accepting traffic from anywhere/HTTP/configure ports
