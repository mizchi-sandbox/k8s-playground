## k8s-playground

- k3s
- node.js server

```bash
# install kubectl by your own way
#   brew install kubernetes-cli
#   gcloud components install kubectl

# start k3s cluster
docker-compose -f k3s-docker-compose.yml up -d # generate kubeconfig.yaml

# set KUBECONFIG to use local k3s
export KUBECONFIG=$(pwd)/kubeconfig.yaml

# apply manifest
kubectl apply -f k8s/ --prune --all
# port-forward to http://localhost:3000
kubectl port-forward svc/myapp-lb 3000:3000
```

Open localhost:3000

## Update k8s/manifest.yaml

Edit `k8s/manifest.yaml`

```
kubectl apply -f k8s/ --prune --all
```

## Build your own server

```
# edit server/index.js
docker build -t <your-name>/node-server .
docker push <your-name>/node-server
```

Edit k8s/manifest.yaml

```yaml
# ...
containers:
  - name: node-app
    image: mizchi/node-server
    ports:
      - containerPort: 3000
```

## LICENSE

MIT
