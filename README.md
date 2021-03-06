# meet-php-fpm-healthcheck

```console
$ echo 127.0.2.1 meet.localhost k3d-registry-meet.localhost \
    | sudo tee --append /etc/hosts

$ k3d registry create registry-meet.localhost \
    --port 5000

$ k3d cluster create meet \
    --servers 1 \
    --agents 3 \
    --port 80:80@loadbalancer \
    --registry-use k3d-registry-meet.localhost:5000

$ docker build app \
    --tag wandersonwhcr/meet

$ docker tag wandersonwhcr/meet \
    k3d-registry-meet.localhost:5000/wandersonwhcr/meet

$ docker push k3d-registry-meet.localhost:5000/wandersonwhcr/meet

$ kubectl apply \
    --filename k8s
```
