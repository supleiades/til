- kubectl get networkpolicy
- kubectl get networkpolicy hello-allow-from-foo -o yaml
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"networking.k8s.io/v1","kind":"NetworkPolicy","metadata":{"annotations":{},"name":"hello-allow-from-foo","namespace":"default"},"spec":{"ingress":[{"from":[{"podSelector":{"matchLabels":{"app":"foo"}}}]}],"podSelector":{"matchLabels":{"app":"hello"}},"policyTypes":["Ingress"]}}
  creationTimestamp: "2021-05-27T05:31:00Z"
  generation: 1
  name: hello-allow-from-foo
  namespace: default
  resourceVersion: "4956"
  selfLink: /apis/networking.k8s.io/v1/namespaces/default/networkpolicies/hello-allow-from-foo
  uid: 63d8bd47-4a3a-41a5-a02c-524507f90b82
spec:
  ingress:
  - from:
    - podSelector:
        matchLabels:
          app: foo
  podSelector:
    matchLabels:
      app: hello
  policyTypes:
  - Ingress
```
