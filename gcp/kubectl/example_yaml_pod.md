- kubectl get pods
- kubectl get pod {pod_name} -o yaml

```yaml
kubectl get pod hello-web -o yaml
apiVersion: v1
kind: Pod
metadata:
  annotations:
    cni.projectcalico.org/podIP: 10.8.0.7/32
  creationTimestamp: "2021-05-27T05:23:31Z"
  labels:
    app: hello
  name: hello-web
  namespace: default
  resourceVersion: "2171"
  selfLink: /api/v1/namespaces/default/pods/hello-web
  uid: 35456aba-b44a-43e6-b07d-40e0e7c11a71
spec:
  containers:
  - image: gcr.io/google-samples/hello-app:1.0
    imagePullPolicy: IfNotPresent
    name: hello-web
    ports:
    - containerPort: 8080
      protocol: TCP
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-5gkrk
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: true
  nodeName: gke-standard-cluster-1-default-pool-ce1ee228-4hgb
  preemptionPolicy: PreemptLowerPriority
  priority: 0
  restartPolicy: Always
  schedulerName: default-scheduler
  securityContext: {}
  serviceAccount: default
  serviceAccountName: default
  terminationGracePeriodSeconds: 30
  tolerations:
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  volumes:
  - name: default-token-5gkrk
    secret:
      defaultMode: 420
      secretName: default-token-5gkrk
status:
  conditions:
  - lastProbeTime: null
    lastTransitionTime: "2021-05-27T05:23:31Z"
    status: "True"
    type: Initialized
  - lastProbeTime: null
    lastTransitionTime: "2021-05-27T05:23:33Z"
    status: "True"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: "2021-05-27T05:23:33Z"
    status: "True"
    type: ContainersReady
  - lastProbeTime: null
    lastTransitionTime: "2021-05-27T05:23:31Z"
    status: "True"
    type: PodScheduled
  containerStatuses:
  - containerID: containerd://aa540bd25321dbe37fd1cceb8e5466e23d0223cd99c16fc40debcd8aafc5d37a
    image: gcr.io/google-samples/hello-app:1.0
    imageID: gcr.io/google-samples/hello-app@sha256:c62ead5b8c15c231f9e786250b07909daf6c266d0fcddd93fea882eb722c3be4
    lastState: {}
    name: hello-web
    ready: true
    restartCount: 0
    started: true
    state:
      running:
        startedAt: "2021-05-27T05:23:32Z"
  hostIP: 10.128.0.4
  phase: Running
  podIP: 10.8.0.7
  podIPs:
  - ip: 10.8.0.7
  qosClass: BestEffort
  startTime: "2021-05-27T05:23:31Z"
```
