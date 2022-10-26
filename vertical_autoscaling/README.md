## Auto scaling

#### How run the application

```shell
docker build . -t tharhtetsanucsm/gpu:latest

docker push tharhtetsanucsm/gpu:latest

# resource requirements
resources:
  requests:
    memory: "50Mi"
    cpu: "500m"
  limits:
    memory: "500Mi"
    cpu: "2000m"

# deploy 

kubectl apply -f deployment.yaml

# metrics

kubectl top pods
```

