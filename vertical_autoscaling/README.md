## Auto scaling

## Kubernetes in GCP
#### Install nvidia driver
```shell
kubectl apply -f https://raw.githubusercontent.com/GoogleCloudPlatform/container-engine-accelerators/master/nvidia-driver-installer/cos/daemonset-preloaded.yaml 
```

#### How run the application in GKE
```shell
docker build . -t tharhtetsanucsm/gpu:latest


docker push tharhtetsanucsm/gpu:latest

# resource requirements
resources:
  limits:
    nvidia.com/gpu: '1'

# deploy 

kubectl apply -f vertical_autoscaling/components/deployment.yaml
kubectl apply -f vertical_autoscaling/components/service.yaml
# metrics

kubectl top pods
```



#### Generate some traffic
```shell
kubectl apply -f vertical_autoscaling/components/application/traffic-generator.yaml

# get a terminal to the traffic-generator
kubectl exec -it traffic-generator sh

# install wrk
apk add --no-cache wrk

# simulate some load
wrk -c 5 -t 5 -d 99999 -H "Connection: Close" http://ths-gpu:8080

#you can scale to pods manually and see roughly 6-7 pods will satisfy resource requests.
kubectl scale deploy/ths-gpu --replicas 2

```