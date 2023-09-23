1. task init
2. task configure
3. deploy gke cluster


> Cilium
```
export NAME="gke-ops"
# Create the node pool with the following taint to guarantee that
# Pods are only scheduled/executed in the node when Cilium is ready.
# Alternatively, see the note below.
gcloud container clusters create "${NAME}" \
 --node-taints node.cilium.io/agent-not-ready=true:NoExecute \
 --zone us-west2-a \
 --cluster-ipv4-cidr=10.1.0.0/19
gcloud container clusters get-credentials "${NAME}" --zone us-west2-a
```

> Without cilium
```
export NAME="gke-ops"
# Create the node pool with the following taint to guarantee that
# Pods are only scheduled/executed in the node when Cilium is ready.
# Alternatively, see the note below.
gcloud container clusters create "${NAME}" \
 --disable-managed-prometheus \
 --zone us-west2-a
```

4. task cluster:verify
5. task cluster:install
6. manual cilium install:

https://docs.cilium.io/en/stable/installation/k8s-install-helm/
https://cloud.google.com/stackdriver/docs/managed-prometheus/setup-managed
