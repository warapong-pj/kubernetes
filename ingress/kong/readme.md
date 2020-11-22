### redeploy kong on kubernetes
1. get ValidatingWebhookConfiguration from cluster with command `ValidatingWebhookConfiguration`
    kubectl get -A ValidatingWebhookConfiguration
    NAME
    nginx-ingress-ingress-nginx-admission

2. delete ValidatingWebhookConfiguration that get from first command `kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-admission`

### how to add private and public key to kubernetes cluster
kubectl create secret tls acm-wemall-dev --key ingress/kong/pri.pem --cert ingress/kong/pub.pem