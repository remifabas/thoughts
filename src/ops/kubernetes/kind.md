# Kind

```admonish tips
[kind](https://kind.sigs.k8s.io/) is a tool for running local Kubernetes clusters using Docker container “nodes”.
kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI.
```

```admonish warning collapsible=true title="install"

If you have go (1.17+) and docker installed  `go install sigs.k8s.io/kind@v0.18.0`

Other way: [here](https://kind.sigs.k8s.io/docs/user/quick-start#installation)

```

````admonish example title="config file" collapsible=true

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
# One control plane node and three "workers".
#
# While these will not add more real compute capacity and
# have limited isolation, this can be useful for testing
# rolling updates etc.
#
# The API-server and other control plane components will be
# on the control-plane node.
#
# You probably don't need this unless you are testing Kubernetes itself.
nodes:
  - role: control-plane
  - role: control-plane
  - role: worker
  - role: worker
  - role: worker
```
````

How to <span style="color: hotpink">create</span> a cluster from a config file:

```
kind create cluster --name local-cluster --config cluster-config.yaml
```

How to <span style="color: hotpink">delete</span> a cluster:

```
kind delete clusters local-cluster
```
