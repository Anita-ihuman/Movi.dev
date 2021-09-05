## Simplify Kubernetes Cluster Management with Kyverno



The introduction of Kubernetes( K8s) was aimed at eliminating the difficulties and complexities encountered when deploying and scaling containerized applications. It has since grown in popularity and appears to be the most talked-about container orchestration tool. Yet, like every other fast-growing technology, K8s had its own downsides, such as configuration complexity, lack of automation, and security challenges with insecure defaults.
![gif.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630831637214/SLHs0uP7o.gif)

To tackle this problem and maintain the standards of K8s, "Kubernetes policy management engines" were introduced by the community. These policy engines would then permit the automation and secure handling of Kubernetes configurations, by regulating configurations and which applications could run within a particular K8s cluster. This need resulted in the development of two CNCF projects and leading policy engines that can be leveraged to manage policies in a Kubernetes environment, [OPA](https://www.openpolicyagent.org/)  and  [Kyverno](https://kyverno.io/) 


## What is a policy engine?
In a Kubernetes(K8s) environment, there are a lot of dynamically moving parts and in order to keep tabs on them, K8s uses the concept of “[policy](https://kubernetes.io/docs/concepts/policy/).” K8 Policies are used to define settings that should be applied across the cluster. Policy engines deliver a number of options in gaining control of Kubernetes resources.

K8s policies are seen in four categories:  [Limit Ranges](https://kubernetes.io/docs/concepts/policy/limit-range/),  [Resource Quotas](https://kubernetes.io/docs/concepts/policy/resource-quotas/),  [Pod Security Policies](https://kubernetes.io/docs/concepts/policy/pod-security-policy/), and  [Process ID Limits and Reservations](https://kubernetes.io/docs/concepts/policy/pid-limiting/).


## What is kyverno?
Kyverno, is an Open source policy engine designed specifically for Kubernetes.
The word "Kyverno" is a Greek word for "Govern". It was originally developed by  [Nirmata](https://nirmata.com/)  and is now a [CNCF](https://www.cncf.io/sandbox-projects/) sandbox project. 

Kyverno allows you to define policies, as Kubernetes resources, that can Validate, Mutate, and Generate other Kubernetes resources. Unlike OPA, which requires you to have an understanding of Rego language in order to define policies, Kyverno is specifically designed to use Kubernetes-style composition and leverage the Kubernetes API metadata to learn the structure of Kubernetes resources. Kyverno uses the YAML files approach and a similar syntax as your K8s resource definitions.


## Why Kyverno?
Well, you must be wondering by now, what makes Kyverno stand out from other policy engines and why it's considered the ideal policy engine.

Let's get to it!.
- **Simplicity **
OPA has its own programming language called [ Rego](https://www.openpolicyagent.org/docs/latest/policy-language/) that is required to work with policies and make decisions.  Kyverno on the other hand makes use of K8s simple declarative approach of writing in Yaml files. This is something almost everyone is likely familiar with already. Kyverno can be used in managing clusters of any size with ease. This provides its users with high flexibility when developing policies.

- **Kubernetes centred**
 Kyverno is a policy engine that was specifically created for Kubernetes to handle the difficulties of managing clusters. Kyverno works well with other existing Kubernetes developer tools, like  [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/),  [Kustomize](https://kustomize.io/), and Git.
- **Generate policies**
Policy engines are created with key capabilities that enable them to validate and mutate policies as needed. Whereas, aside from Kyverno's Kubernetes-native design, it possesses the ability to[generate policies](https://kyverno.io/policies/?policytypes=generate). You can now leverage the same engine to Validate, mutate and Generate any resource.

All these put together, are what make Kyverno simple, yet powerful, compared to other policy engines.

## How does Kyverno work?
Kyverno runs as a  [dynamic admission controller](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/)  in a Kubernetes cluster.
There are two relevant built-in admission controllers in K8s, *ValidatingAdmissionWebhooks* and *MutatingAdmissionWebhooks*. The two admission controllers receive an action from the REST endpoint of a service running inside the cluster that is Kyverno. Based on this received action, these admission controllers return results that enforce admission policies or reject requests.

Kyverno policies can match resources using the resource kind, name, and label selectors. Wildcards are supported in names.

![kyverno-architecture.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630765432725/C103ddGlJ.png)

> 
To better understand how Kyverno works, let's break it down with a non-technical instance.

Imagine a firm with two receptionists (admission controllers - *ValidatingAdmissionWebhooks* and *MutatingAdmissionWebhooks*). When a package(Kubernetes API requests) is delivered for the CEO, these receptionists will each carry these packages to the manager(Kyverno). The manager now will review the packages delivered and cross-check to make sure the packages delivered meet the specifications(policies you have written) directed by the CEO. These packages are examined based on the name on the package, the sender, the labels, and the kind of package it is.

After scrutinizing these packages, the manager will then send the final decision concerning the packages as feedback to these receptionists (ValidatingAdmissionWebhooks and MutatingAdmissionWebhooks). The receptionists can then go ahead and carry out the necessary actions that need to be taken, like stamping the packages or make some notes on the packages received.


## Conclusion
If you are still reading this, that means this project interests you too. 
Good news! it is an Open-source Project, so you are welcome to explore the [GitHub repository](https://github.com/kyverno/kyverno) and make your contributions as well also, don't forget to [Star the project](https://github.com/kyverno/kyverno/stargazers). You can also join the [Kyverno slack channel](https://slack.k8s.io/#kyverno) to connect with the maintainers and other Kyverno community members. You can also join us at any one of the monthly [Kyverno community meetings](https://docs.google.com/document/d/10Hu1qTip1KShi8Lf_v9C5UVQtp7vz_WL3WVxltTvdAc/edit#heading=h.ulc3pq1azmlq)!

### References
- [Kyverno Documentation](https://kyverno.io/docs/introduction/)
- [Kubernetes Documentation](https://kubernetes.io/docs/concepts/policy/)
- [how-kubernetes-policies-work-and-when-they-dont-scale](https://thenewstack.io/how-kubernetes-policies-work-and-when-they-dont-scale/)
- [kyverno-vs-opa-modernizing-your-kubernetes-policy-management](https://hakin9.org/kyverno-vs-opa-modernizing-your-kubernetes-policy-management-by-ritesh-patel/)
- [CNCF Sandbox Projects](https://www.cncf.io/sandbox-projects/)
- [what-is-kyverno-and-how-can-it-simplify-managing-k8s-clusters](https://www.educative.io/edpresso/what-is-kyverno-and-how-can-it-simplify-managing-k8s-clusters)
- [how-explain-kubernetes-plain-english](https://enterprisersproject.com/article/2017/10/how-explain-kubernetes-plain-english)
