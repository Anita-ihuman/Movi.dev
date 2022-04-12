## Apache APISIX Ingress Controller Over the K8s Native Ingress

### What is Ingress?

An ingress is an API object that allows access to your Kubernetes services from outside the Kubernetes cluster by defining the edge-entry traffic routing rules (e.g. load balancing, SSL termination, path-based routing, protocol). The ingress manages external access to the services within a cluster using public IP and port mapping.

The component responsible for carrying out this action is called the Ingress controller.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1649772100803/4IArmUThS.png)

### Role of K8s Ingress Controller in a Cluster?

In a Kubernetes application, pods run inside a cluster while a load balancer runs outside. The load balancer is responsible for accepting connections from the internet and routing them to an edge proxy located within your cluster. This edge proxy is in charge of routing traffic into your pods. You can route multiple back-end services through a single IP address using ingress.

An ingress controller is a third party edge-proxy that implements ingress. They are responsible for reading the Ingress Resource information and processing that data accordingly. The ingress controller does not replace the load balancer; instead, it adds a layer of routing and control behind the load balancer.

*   It aids in the consolidation of routing rules into a single location.
*   It is declared, created, and destroyed independently from the services you wish to expose.
*   It is configured using the Kubernetes API to deploy objects called “Ingress Resources.”

### The Drawbacks

Kubernetes provides several methods for exposing edge interfaces, including node port, load balancer, ingress, etc. Ingress is unquestionably a more cost-effective way to use reverse proxies as it reveals a limited number of public IPs. However, it is accompanied by specific risks like complexity, latency, and security once implemented. These issues are frequently intertwined; the others will likely be if one is present.

**Complexity:**

Microservice architectures are built with ​​lightweight and simple designs, and this is a feature most organizations look out for in their application. However, the K8s ingress does not stick to these principles, as it is developed mainly using complex scripts and functions. This results in complexities for the underlying engine it is implemented on and even more confuses the configurator. Kubernetes being an overcomplicated tool, having to implement other complex features might affect your application’s scalability and overall performance.

**Lack of support for stateful load balancing:**

Kubernetes is an operation and maintenance-oriented non-business management system. As a result, complex load balancing solutions such as session persistence are not supported. It also does not support these contradicting load balancing solutions in the short run.

Google has already attempted to address this issue with its service mesh solution ([istio](https://istio.io/)). The istio architecture is flawless. However, it compromises performance, which can be remedied using its mixer v2.

**Dynamic adjustment of weights:**

It is tricky to control traffic by percentage in Kubernetes, although this is one feature most organizations look out for. However, after v1.8, Kubernetes began supporting [IPVS](https://en.wikipedia.org/wiki/IP_Virtual_Server) as a Kube-proxy startup parameter or Kube-route’s annotation.

**Weak scalability:**

Although developers created ingress to tackle edge traffic, people’s desire for managing edge traffic is equal to or greater than their need for internal traffic.

Business-level grayscale control, fusing, flow control, authentication, and flow control are the basic requirements popular on ingress. However, native ingress extension is limited in these aspects.

**Reload problem:**

The YAML configuration file is analyzed by the ingress controller, transformed to Nginx.conf, and then triggered to reload Nginx.conf to make the setting take effect in the architecture of Kubernetes native ingress.

Routine operation and maintenance inevitably touch the ingress YAML configuration occasionally. Every time the configuration takes effect, it will trigger a reload. It is unacceptable, primarily when edge traffic uses long connections, which are more likely to cause accidents.

### Why Apache APISIX Ingress Controller?

APISIX Ingress is another Ingress Controller implementation. APISIX Ingress differs from Kubernetes Ingress Nginx in that it uses Apache APISIX as the actual data plane for business traffic. Using Apache APISIX as an ingress implementation can help address the above drawbacks while also providing the community with an additional ingress controller option.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1649772103547/rhxrheSRf.png)

**Tackles the complexities:**

In Apache APISIX, we can write logic through plug-in code to expose a simple configuration interface, which is convenient for configuration maintenance and avoiding the interference of scripts to configuration personnel.

**Support for stateful load balancing:**

Apache APISIX natively supports load balancing such as session persistence and reserves the expansion capability of the balancer stage. Since Kubernetes permits project expansion, it is possible to enlarge the advanced load balancing requirements based totally on Apache APISIX.

**Dynamic in nature:**

Apache APISIX abstracts main objects like route, service, consumer, upstream, plug-in, and so on, and operations like weight adjustment are naturally supported. Hence, changing the node weight under upstream.

**Ability to expand:**

In terms of expansion capabilities, Apache APISIX supports plug-ins. In addition to the officially offered plug-ins, you can create custom plug-ins to satisfy your specific needs.

**Hot reload:**

Apache APISIX supports hot configuration, and routes can be defined and modified at any time without triggering Nginx reload. So whether you add, delete or alter plug-ins and update codes of plug-ins within the disk, you don’t need to restart the service.

### Implementing APISIX Ingress Controller in AISpeech

[AI Speech](https://www.linkedin.com/company/al-speech-ltd) is a leading speech technology platform. It specializes in computer speech recognition, tone analysis, and dialogue management techniques.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1649772105766/hbZwJwqi1.png)

The timing diagram

To implement the Apache APISIX ingress controller, AISpeech considered two challenges that required immediate attention.

*   To synchronize the state of the Kubernetes cluster and Apache APISIX.

The [Apache APISIX ingress controller](https://github.com/apache/apisix-ingress-controller) project addresses this by syncing Kubernetes pod information with the upstream in APISIX. Simultaneously, the primary and backup systems are constructed to manage their high-availability issues.

*   To define the objects in Apache APISIX in Kubernetes Custom Resource Definitions([CRD](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)).

The Apache APISIX ingress provides CRD support to understand declarative configurations better. State checking, however, ensures quick access to the synchronized state of declarative configurations. Because Kubernetes declares the cluster state using YAML, the CRD must be defined in Apache APISIX for the objects (route/service/upstream/plug-in) to integrate into Kubernetes.

### Conclusion

There are several popular Ingress Controllers for Kubernetes, but choosing the right one for your application is always tricky. As your application scales, you need to consider an ingress controller that aligns with your Kubernetes application in testing and production mode. The [Apache APISIX ingress controller](https://github.com/apache/apisix-ingress-controller) is an open-source project that answers all these needs.