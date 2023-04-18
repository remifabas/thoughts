# Architecture Overview

~~~admonish warning title="Warning" collapsible=true
this documentation is a substrate / personal synthesis with less information than the official documentation of kuerbenetes which can be found [here](https://kubernetes.io/docs/concepts/overview/components/)
~~~

![Components](img/components-of-kubernetes.svg)

~~~admonish info title="Kubernetes Cluser" collapsible=true
A Kubernetes cluster is a set of worker machines, called nodes, that run containerized applications.

This cluster consist in two nodes family, the workers and the control-plane.
- The control plane handle and manage the worker nodes and the Pods in the cluster.
- The worker node(s) is the machine(s) where your applications workload will be deployed.

Warning : the image here does not show that the control plane is also running in nodes !
~~~

~~~admonish bug title="Pods, Workload ?" collapsible=true
About kubernetes wording:  
- Workload: It's an app running on Kubernetes. It could be a single component or several that work together.
- Pods: Smallest deployable units of computing that you can create and manage in Kubernetes. It's a group of one or more containers.
~~~

## Control Plane

The control plane's components make global decisions about the cluster. Control plane components can be run on any machine in the cluster. However, for simplicity, set up scripts typically start all control plane components on the same machine, and do not run user containers on this machine.

~~~admonish title="kube-apiserver" collapsible=true
Expose the kubernetes API, front end for control plane. Kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances.
Kube-api-server run in a pod, for each vm in control plane. You can find these pods with 

`kubectl get po -o wide -n kube-system | grep apiserver`
~~~

~~~admonish title="etcd" collapsible=true
Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data. This store run in multiples pods in control plane.
You can find these pods with  
`kubectl get po -o wide -n kube-system | grep etcd`
~~~

~~~admonish title="kube-scheduler" collapsible=true
Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.
Factors taken into account for scheduling decisions include: individual and collective resource requirements, hardware/software/policy constraints, affinity and anti-affinity specifications, data locality, inter-workload interference, and deadlines.
You can find these pods with  
`kubectl get po -o wide -n kube-system | grep scheduler`
~~~

~~~admonish title="kube-controller-manager" collapsible=true
Control plane component that runs <span style="color: hotpink">controller</span> processes. I will explain [operator](https://iximiuz.com/en/posts/kubernetes-operator-pattern/) and [controller](https://kubernetes.io/docs/concepts/architecture/controller/) later.
Some types of these controllers are:

- Node controller: Responsible for noticing and responding when nodes go down.
- Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
- EndpointSlice controller: Populates EndpointSlice objects (to provide a link between Services and Pods).
- ServiceAccount controller: Create default ServiceAccounts for new namespaces.

`kubectl get po -o wide -n kube-system | grep controller-manager`
~~~

~~~admonish title="cloud-controller-manager" collapsible=true
The cloud controller manager lets you link your cluster into your cloud provider's API, and separates out the components that interact with that cloud platform from components that only interact with your cluster.
~~~

## Nodes

Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.

~~~admonish title="kubelet" collapsible=true
Agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.

Kubelet run as process on each node in the cluster, rather than running inside a pod like etcd, apiserver.
~~~

~~~admonish title="kube-proxy" collapsible=true
kube-proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes [Service](services.md) concept.

kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.

kube-proxy uses the operating system packet filtering layer if there is one and it's available. Otherwise, kube-proxy forwards the traffic itself.

`kubectl get po -o wide -n kube-system | grep kube-proxy`
~~~

~~~admonish title="Container runtime" collapsible=true
The container runtime is the software that is responsible for running containers.

Kubernetes supports container runtimes such as containerd, CRI-O, and any other implementation of the Kubernetes [CRI](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-node/container-runtime-interface.md) (Container Runtime Interface).
~~~

## Addons

Addons use Kubernetes resources (DaemonSet, Deployment, etc) to implement cluster features. Because these are providing cluster-level features, namespaced resources for addons belong within the kube-system namespace. List of [addons](https://kubernetes.io/docs/concepts/cluster-administration/addons/)

~~~admonish title="DNS" collapsible=true
While the other addons are not strictly required, all Kubernetes clusters should have [cluster DNS](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/), as many examples rely on it.

Cluster DNS is a DNS server, in addition to the other DNS server(s) in your environment, which serves DNS records for Kubernetes services.
~~~
