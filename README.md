# meet-php-fpm-healthcheck

```console
$ k3d cluster create meet \
    --servers 1 \
    --agents 3 \
    --port 80:80@loadbalancer \
    --registry-create registry:registry.meet.localhost:5000

$ docker build app \
    --tag registry.meet.localhost:5000/wandersonwhcr/meet
```
