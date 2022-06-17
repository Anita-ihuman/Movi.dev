## Introducing Container Orchestration Using Kubernetes

Container orchestration is slowly becoming the trend of the day, and Kubernetes is leading the chain. We cannot talk about Container Orchestration(Kubernetes and its fundamentals) without having a basic understanding of containerized services. In the previous blog post, I introduced containerized platforms and how the concept of containers is introduced. 

If you haven't already, do consider reading my blog post on" [The Beginners Intro to Containerized Platforms: Docker"](https://movi.hashnode.dev/the-beginners-intro-to-containerized-platforms-docker-ckt9rvjdr0boa98s170rm7i6i).
In this article, I will explain what container orchestration is about, what Kubernetes is, its problems with containers, and its core concepts.

## What was the problem?
Recently, most big applications have been broken down into smaller, independently running components called  [microservices](https://microservices.io/). These microservices can be quickly developed, deployed and updated individually to meet the rapidly changing technology requirements. 
There has been a rise in microservices, and this has caused an increased usage of container technologies. This is because containers offer the perfect host for small independent components like microservices.

Like every new technology, containerized applications were growing more complex. Manually handling these applications across multiple environments soon became increasingly difficult to configure, manage, and keep the whole system running smoothly. This created the need for container orchestration technologies(  [Kubernetes](https://kubernetes.io/) ).

## Container Orchestration:
This solution consists of a set of tools and scripts that help host containers in a production environment. Container orchestration is the automation of operational efforts like Deployment, management, scaling, load balancing and networking required to run containerized workloads. It helps to deploy an application across different environments without any interruptions or the need to redesign it.


![orchestrator diagram.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631292657590/QTPn0aiZr.png)
 [Img source](https://scoutapm.com/blog/container-orchestration-in-2019) : Ochestration
## Introducing Kubernetes
Kubernetes is an open-source container orchestration tool developed by Google. It helps to manage, automate deployment and scale containerized applications. This means that Kubernetes(K8s) manages applications that are made up of hundreds of containers in different environments like virtual, physical and hybrid. K8s control how and where those containers will run.

The name Kubernetes is a Greek word for **pilot **or **helmsman** (the person holding the ship's steering wheel). It is often abbreviated as K8s for simplicity because of the eight letters in-between "K" and "s".

Of course, K8s is not the only orchestration tool out there; there are tools like  [Docker Swarm](https://docs.docker.com/engine/swarm/),  [Apache Mesos](http://mesos.apache.org/),  [Marathon](https://mesosphere.github.io/marathon/), and others. 
So, what exactly makes K8s stand out?


![3-528x269.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631294998244/D29n9pgmp.png)
** Why is Kubernetes so popular?**

Google initially owned Kubernetes until it was open-sourced in 2014; it was later donated to the  [CNCF](https://www.cncf.io/). The container management tool soon gained popularity and has dominated the open-source community. Kubernetes has the support of  [Red Hat](https://www.redhat.com/),  [AWS](https://aws.amazon.com/),  [Google](https://www.google.com/),  [IBM](https://www.ibm.com/eg-en/cloud)  and other big companies contributing to it.
### Solutions  Kubernetes offers
In recent applications, developers have been seeking ways to avoid any form of downtime to applications. So much so that even while updates are in progress on an application, users do not experience any interruption to the application's services. This is possible because containerized applications consist of everything an app requires to run smoothly. 
 
Kubernetes provides the following:

- **Storage orchestration:**

  With Kubernetes, you can automatically mount a storage system of your choice, whether it be locally, with a cloud provider such as AWS or GCP, or a network storage system
- **Self-Healing:**

 In Kubernetes, when a container fails, Kubernetes is capable of restarting it. Kubernetes can eliminate containers that do not respond to the user-defined troubleshooting. And it also replaces the malfunctioning containers with new ones. 
- **Load balancing and service discovery:**

 Kubernetes enables load balancing by offering a single DNS name for a batch of containers. So, you don't have to redesign the applications to use any service discovery mechanism.
- **Unceasing Integration Workloads:**

 Kubernetes can monitor and control all the continuous integration workloads
- **Secret and configuration management:**

 Kubernetes lets you store and manage sensitive information, such as passwords, OAuth tokens, and SSH keys. You can deploy and update secrets and application configuration without rebuilding your container images and leaving your secrets exposed and vulnerable to security risks.


## Concepts on Kubernetes 
The purpose of Kubernetes is to host your applications in the form of containers in an automated fashion. To enable you to deploy as many instances of your application as required and ease communication between different services within your application.

![full-kubernetes-model-architecture.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631291777922/0P57ixj5K.png)
 [Img Source](https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams):  *Kubernetes Architecture*
  ### Master Node: 
The Master node is responsible for managing the Kubernetes cluster, storing information regarding the different nodes, planning which containers are distributed, and monitoring the nodes and containers on them. The master node can do this using a set of components called the **control plane**.
![images (1).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631293556275/H_NJPUIom.png)
 [Img source](https://www.researchgate.net/figure/Kubernetes-Master-Looking-deeper-into-the-architecture-a-master-node-in-kubernetes_fig1_344406507) : Master node
  ### API server:
 The Kube-API is the front end of the Kubernetes control plane, handling internal and external requests. To interact with the Kubernetes cluster, you need the Kubernetes API server.

  ### etcd server: 
The etcd is a database that stores configured information regarding the Cluster in a key-value format. The etcd holds every information you need about the multiple nodes and stores it distributed, avoiding conflicts.


  ### Kube-controller-manager: 
These are considered the brain behind orchestration. The controller manager contains several controller functions in one. They are responsible for noticing and responding when a node, container or endpoint goes down or dies. One of the controllers contacts the scheduler to ensure the correct number of pods is running. If a pod is down, another controller will notice and bring up a new pod in cases like this.

  ### Scheduler:
 A scheduler is responsible for distributing work or containers across multiple nodes based on the Cluster's health. It identifies the right Node to place a container based on the container's resource requirements, the worker node's capacity or any other policies.

## Basic Terminologies in Kubernetes
- **Node: **A node is a machine, either physical or virtual, on which Kubernetes is installed. Nodes have everything necessary to run your application containers, including the container runtime( [Docker](https://www.docker.com/) ) and  [Kubletes](https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/)  services installed. A node is a worker machine where K8s launch containers. Nodes were formerly known as minions. A machine requires more than one Node for backup

- **Cluster: **A cluster is a set of nodes grouped; this way, even if one Node fails, you will still be able to access the other nodes. 

- ** Master:** 
This is the Node with a collection of components that make up the control plane of  Kubernetes. A master node watches over the nodes in the Cluster. It is responsible for the actual orchestration of containers on the worker nodes.

- **Minikube:** 
This is an open-source tool that runs on a virtual box on a system. It is a node cluster where master and worker processes run on a node. Minikube enables you to run Kubernetes on your local machine.

- **Pod: ** 
This is the smallest deployable unit of K8s; it is considered an abstraction over a container. 
The pod creates a running environment over the container. The pod represents a single instance of an application and is responsible for the running of containers. Every pod holds at least one container and governs the execution of that container. When the container exits, the pod dies.
- **ReplicaSets**: 
 The replicaSets ensure that a set of identically configured pods runs at the desired replica count. If a pod fails, a replica set will bring up another pod as a replacement.
- **Secrets:**  
Secrets are used on very sensitive information so that it's accessible when necessary to pods in your Cluster but protected from unnecessary visibility. They are used to store non-public information such as token certificates or passwords. They are attached to pods at runtime so the sensitive configuration data can be stored securely in a cluster. 
- **Deployment:**
 This is a higher-order abstraction that controls the deploying and maintaining sets of pods behind the scene. Deployments offer a sophisticated logic for deploying, updating and scaling pods. They make use of a replica set as a building block. This adds the feature of life cycle management
- **Ingress**: ingresses provide a way to manage external access to the services within a cluster. One single external ingress point can accept traffic destined to many different internal surfaces within the Cluster.

![ingress.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631294300457/H7y4E_YD2.png)
- **Kubectl**: This is a command-line interface used to manage and deploy applications in a Kubernetes cluster. Kubectl does this by communicating with the Kubernetes API.

## Conclusion 
Phew😅 !!

If you have read so far, congratulations, you now understand Container Orchestration and an idea of what Kubernetes is all about. In my subsequent blog post, I will be bringing more content on Kubernetes. For a more comprehensive understanding of Kubernetes, check out these resources below. 

### References
- [kubernetes-in-action](https://www.manning.com/books/kubernetes-in-action)
- [ubernetes-best-practices](https://www.weave.works/blog/kubernetes-best-practices)
- [kubernetes-bootcamp](https://kubernetesbootcamp.github.io/kubernetes-bootcamp/)
- [kubernetes-for-dummies](https://dev.to/stevenmcgown/kubernetes-for-dummies-5hmh) 
- [how-explain-kubernetes-plain-english](https://enterprisersproject.com/article/2017/10/how-explain-kubernetes-plain-english)
- [Terraform Best Practices for Better Infrastructure Management](https://spacelift.io/blog/terraform-best-practices)
- [kubernetes-Documentation](https://kubernetes.io/docs/setup/)
- [kubernetes-tutorial](https://www.guru99.com/kubernetes-tutorial.html)
- [kubernetes-vs-docker](https://azure.microsoft.com/en-us/topic/kubernetes-vs-docker/)
- [kubernetes-101-concepts-and-why-it-matters](https://www.magalix.com/blog/kubernetes-101-concepts-and-why-it-matters)
- [15 Kubernetes Best Practices Every Developer Should Know](https://spacelift.io/blog/kubernetes-best-practices)