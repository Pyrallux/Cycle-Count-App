# Azure/Docker Build and Deploy Commands

## Backend

```sh
docker build --secret id=django-private-key.txt,src="../django-private-key.txt" -t pyrallux/ccbb-backend:latest .
docker tag pyrallux/ccbb-backend:latest ccbbtestreg.azurecr.io/ccbb-backend:latest
docker push ccbbtestreg.azurecr.io/ccbb-backend:latest
docker run -v .:/run/secrets -p 8000:8000 pyrallux/ccbb-backend:latest
```

## Webserver

```sh
docker build -t pyrallux/ccbb-frontend:latest .
docker tag pyrallux/ccbb-frontend:latest ccbbtestreg.azurecr.io/ccbb-webserver:latest
docker push ccbbtestreg.azurecr.io/ccbb-webserver:latest
docker run -p 80:80 pyrallux/ccbb-frontend:latest
```

## Azure Container Registry

```sh
az login
az acr login --name ccbbtestreg
```

### Azure Portal Setup

#### Secret Volumes

- Container App -> Settings -> Secrets -> Configure All Secrets Needed
- Container App -> Revisions and replicas -> Volumes -> Add -> Secret/(name)/(Configure All Secrets Needed)
- Container App -> Revisions and replicas -> Create new revision -> Container -> Select Container -> Volume Mounts -> (Configure to mount secret volume)

#### Ingress/Networking

- Container App -> Settings -> Ingress -> Enabled/Accepting traffic from anywhere/HTTP/configure ports
