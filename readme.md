## github package repostiry(Personal access tokens)
### how to generate token
1. goto github.com and click myproject
2. on right coner click as picture profile and choose Settings
3. click on menu Developer settings > Personal access tokens and Generate new token

### add authentication to docker
echo -n $TOKEN | docker login https://docker.pkg.github.com -u USERNAME --password-stdin

### add authentication to kubernetes
echo -n $TOKEN | base64
echo '{"auths":{"docker.pkg.github.com":{"auth":"<AUTH>"}}}' | kubectl create secret generic github-com --type=kubernetes.io/dockerconfigjson --from-file=.dockerconfigjson=/dev/stdin