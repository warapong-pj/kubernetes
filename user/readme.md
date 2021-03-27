# Create user to limit access cluster  
1. kubectl create serviceaccount developer -n default
2. kubectl apply -f role.yml
3. kubectl describe secrets "$(kubectl describe serviceaccount developer -n default | grep -i Tokens | awk '{print $2}')" -n default | grep token: | awk '{print $2}'
4. export TOKEN=$(kubectl describe secrets "$(kubectl describe serviceaccount developer -n default | grep -i Tokens | awk '{print $2}')" -n default | grep token: | awk '{print $2}')
5. kubectl config set-credentials developer --token=$TOKEN
6. kubectl config set-context developer --cluster=kubernetes --user=developer
7. kubectl config use-context developer

# Switch to admin cluster
1. kubectl config use-context kubernetes-admin@kubernetes