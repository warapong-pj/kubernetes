command to generate istio yaml file
istioctl manifest generate --set values.global.jwtPolicy=first-party-jwt > ingress/istio/istio.yml 