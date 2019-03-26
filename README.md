# Proxier

Proxier is a better approach to expose applications in Kubernetes. It supports load balancing to a set of pods with weights and provides high-performance load balancing with nginx and HAProxy.

+ supports canary deployment and load balancing by weight
+ scales horizontally with pressure by default
+ builtin load balancing applications support, ex: nginx and HAProxy

```yaml
apiVersion: maegus.com/v1
kind: Proxier
metadata:
  name: example-proxier
spec:
  ports:
    - name: http
      protocol: TCP
      port: 80
  selector:
    app: example
  backends:
    - name: v1
      weight: 90
      selector:
        version: v1
    - name: v2
      weight: 9
      selector:
        version: v2
```

## Architecture overview

![proxier-architecture](./images/proxier-architecture.png)

## Installation

```
kubectl apply -f https://raw.githubusercontent.com/draveness/proxier/master/deploy/deploy.yaml
```

## Usage

## License

MIT License, see [LICENSE](./LICENSE)
