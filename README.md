# Kubernetes-in-ML-systems

#### How run the application

```shell
docker build . -t "gpu"
docker run -it --gpus all -d --env PORT=8080 --env _SERVER="stg" -p 5000:8080 gpu
```

