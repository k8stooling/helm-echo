This is a very simple helm chart to deploy a quick echo service with jmalloc/echo-server.

It is setting securityContext and resources by default, so that you spare some iterations on restricted environments.

A simple values file looks like this to enable ingress:

```yaml

ingress:
  enabled: true
  className: # your ingressClassName
  annotations:
    # your ingress controller, cert manager or external-dns related annotations
    hello: world
  hosts:
    - host: echo.example.com
      tls_secret: echo-tls
      paths:
        - path: /
          pathType: ImplementationSpecific
  tls: true

```

**Installation**

```bash

helm upgrade --install oci://ghcr.io/k8stooling/charts/echo --version 2025.01.27

```
