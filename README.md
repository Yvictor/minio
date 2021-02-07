# mlflow 
mlflow deployment 

### traefik

```
docker network create --driver=overlay traefik-public

export NODE_ID=$(docker info -f '{{.Swarm.NodeID}}')

docker node update --label-add traefik-public.traefik-public-certificates=true $NODE_ID

export EMAIL=yvictor3141@gmail.com
export TRAEFIK_DOMAIN=traefik.yvictor.ml
export USERNAME=admin
export PASSWORD=changethis
export HASHED_PASSWORD=$(openssl passwd -apr1 $PASSWORD)
docker stack deploy -c traefik.yml traefik
```

## portainer
```
export DOMAIN=yvictor.ml
export STACK_NAME=portainer
docker stack deploy -c portainer.yml portainer
```

## minio

```
export DOMAIN=yvictor.ml
export STACK_NAME=minio
docker stack deploy -c minio.yml minio
```

## mlflow

```
source .env
export DOMAIN=yvictor.ml
export STACK_NAME=mlflow
docker stack deploy -c mlflow.yml mlflow
```