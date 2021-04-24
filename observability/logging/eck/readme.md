# Install CRD
kubectl apply -f https://download.elastic.co/downloads/eck/1.4.1/all-in-one.yaml  

# Get elastic password
kubectl get secret logging-es-elastic-user -o=jsonpath='{.data.elastic}' | base64 --decode; echo  

# How to send log to Logstash
```
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: app
  annotations:
    kubernetes.io/ingress.class: "kong"
    konghq.com/plugins: "eck"
spec:
  rules:
  - host: app.demo.local
    http:
      paths:
      - path: /
        backend:
          serviceName: app
          servicePort: 80
```

# Deploy Fluent Bit
```
kubectl create namespace logging
kubectl create -f https://raw.githubusercontent.com/fluent/fluent-bit-kubernetes-logging/master/fluent-bit-service-account.yaml
kubectl create -f https://raw.githubusercontent.com/fluent/fluent-bit-kubernetes-logging/master/fluent-bit-role.yaml
kubectl create -f https://raw.githubusercontent.com/fluent/fluent-bit-kubernetes-logging/master/fluent-bit-role-binding.yaml

kubectl create -f https://raw.githubusercontent.com/fluent/fluent-bit-kubernetes-logging/master/output/elasticsearch/fluent-bit-configmap.yaml
kubectl create -f https://raw.githubusercontent.com/fluent/fluent-bit-kubernetes-logging/master/output/elasticsearch/fluent-bit-ds.yaml
```