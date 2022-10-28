# Kubernetes-in-ML-systems

#### How run the application

```shell
docker build . -t "gpu"
docker run -it --gpus all -d --env PORT=8080 --env _SERVER="stg" -p 5000:8080 gpu
```

## Kubernetes in GCP
#### Install nvidia driver
```shell
kubectl apply -f https://raw.githubusercontent.com/GoogleCloudPlatform/container-engine-accelerators/master/nvidia-driver-installer/cos/daemonset-preloaded.yaml 
```