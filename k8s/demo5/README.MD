# Service Mesh

## Demo5

### Aim

- Demo Dark Traffic in order to test new applications release with real datas

### Deployment

Remove Previous VirtualService:

```sh
istioctl delete -f demo4/virtualservice-delay.yml
```

Scale down demo-istio-v2:

```sh
kubectl scale deployment demo-istio-v2 --replicas=2
```

Apply virtual sercice:

```sh
istioctl create -f demo5/virtualservice-mirror.yml
```

### Usage

Curl your application demo-istio and see logs/traffic and demo-istio-v2:

```sh
curl http://<REDACTED>/mirror/healthz -vv
```

```sh
stern --selector app=demo-istio-v2
```

```sh
stern --selector app=demo-istio
```

### Notes

### Todo