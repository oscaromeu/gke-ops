1. task init
2. task configure
3. deploy gke cluster

```
export NAME="$(whoami)-$RANDOM"
# Create the node pool with the following taint to guarantee that
# Pods are only scheduled/executed in the node when Cilium is ready.
# Alternatively, see the note below.
gcloud container clusters create "${NAME}" \
 --node-taints node.cilium.io/agent-not-ready=true:NoExecute \
 --zone us-west2-a
gcloud container clusters get-credentials "${NAME}" --zone us-west2-a
```

4. task cluster:verify
5  task cluster:install 
