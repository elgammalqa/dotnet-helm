## Helm

```
brew install kubernetes-helm
brew install kubectl
```

## Development

- https://dev.to/wolnikmarcin/run-asp-net-core-3-on-kubernetes-with-helm-1o01
- http://localhost:5000/WeatherForecast
- http://localhost:80/WeatherForecast
- http://localhost:9999/WeatherForecast

*Build*

```bash
minikube start
eval (minikube docker-env)
docker image build --pull -t aspnet3k8s:v1 .
```

*Start*

```bash
helm install aspnet3release ./chart
kubectl port-forward service/aspnet3release-service 9999:8888
```

*Release*

```bash
helm upgrade aspnet3release ./chart --values ./chart/production-values.yaml
```

*Check*

```bash
kubectl get pods
kubectl get all --selector app=aspnet3core
helm uninstall aspnet3release

```

*Log*

```
kubectl get pods
kubectl describe pod aspnet3release-deployment-6556b59489-v4gj7
kubectl -n kube-system logs -f podname
```