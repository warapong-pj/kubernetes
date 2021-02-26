### add authentication to docker
echo -n $TOKEN | docker login https://docker.pkg.github.com -u USERNAME --password-stdin

### add authentication to kubernetes
echo -n $TOKEN | base64
echo '{"auths":{"docker.pkg.github.com":{"auth":"<AUTH>"}}}' | kubectl create secret generic github-com --type=kubernetes.io/dockerconfigjson --from-file=.dockerconfigjson=/dev/stdin

### expose ingress to external
1. curl -L https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip -o ngrok.zip
2. unzip ngrok.zip
3. ./ngrok http -bind-tls=true -region=ap -host-header=demo.local 192.168.1.240