generate istio operator
- istioctl operator init

step to deploy istio operator
1. kubectl apply -f istio-operator.yml
2. kubectl apply -f istio.yml
3. kubectl label namespace default istio-injection=enabled # command to inject sidecar proxy