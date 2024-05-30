# ⚒️ K8S: Fundamentals Concepts

## What Kubernetes is?

Kubernetes effectively acts as a "Cloud Operating System" for distributed systems or applications running on a cluster of physical or virtual machines, specifically designed to manage large groups of containerised applications.

## What Kubernetes does?

**Abstraction:** Kubernetes creates a unified interface for applications, shielding them from the underlying infrastructure complexities. Whether apps run on physical servers on premise, virtual machines in the cloud, or a mix of both, Kubernetes provides a consistent environment. This makes it easier to move and scale apps.

**API-Driven Interaction:** Everything in Kubernetes is controlled through its API. This makes it easy to integrate with your existing IT tools and workflows. You can use command-line tools, graphical interfaces, or even write scripts to automate tasks and interact with a Kubernetes environment.

**Orchestration:** Kubernetes automates the entire lifecycle of applications – from deployment and scaling to updates and self-healing. It monitors the health of applications and infrastructure, restarting or replacing components as needed to keep everything running smoothly.

**Resource Management:** Kubernetes acts like a traffic controller, dynamically allocating resources like CPU, memory, and storage to applications. It optimizes the utilisation of infrastructure, ensuring  apps get the resources they need while preventing resource waste.

## Main Components of a Kubernetes Cluster

<figure><img src=".gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

1. **Control Plane**:
   * The control plane manages the state of the Kubernetes cluster, including scheduling and responding to cluster events.
2. **API Server**:
   * Acts as the frontend to the cluster, exposing the Kubernetes API and serving as the gateway for all internal and external communications.
3. **etcd**:
   * A lightweight, distributed key-value store that stores all cluster data, ensuring there is a single source of truth for the state of the cluster.
4. **Scheduler**:
   * Responsible for assigning work, such as Pods, to Nodes based on resource availability and other constraints.
5. **Controller Manager**:
   * Runs controller processes to regulate the state of the cluster, managing routine tasks such as replicating components and handling node operations.
6. **Kubelet**:
   * An agent running on each node, ensuring that containers are running in a Pod and healthy as per the specifications.
7. **Kube Proxy**:
   * Maintains network rules on nodes, allowing network communication to Pods from network sessions inside or outside of the cluster.
8. **Container Runtime**:
   * The software responsible for running containers, with Docker being the most known example, though Kubernetes supports several alternatives.

## Fundamentals Concepts of Kubernetes

1. **Pods**:
   * The smallest deployable units in Kubernetes, each Pod represents a single instance of a running process in your cluster.
2. **Nodes**:
   * These are the worker machines within a Kubernetes cluster, which can be either physical or virtual systems.
3. **Clusters**:
   * Comprises a group of nodes that work together to run containerised applications. Kubernetes manages these applications across the cluster.
4. **Services**:
   * A Service in Kubernetes defines a logical set of Pods and a policy by which to access them, often through a stable IP address.
5. **Deployments**:
   * Manage the desired state of Pods declaratively, facilitating updates and scaling for applications.
6. **Namespaces**:
   * Virtual clusters within the same physical cluster, Namespaces are used to divide cluster resources among multiple users.
7. **ConfigMaps and Secrets**:
   * ConfigMaps handle non-confidential configuration data, whereas Secrets manage sensitive information. Both separate configuration from application code.
8. **Persistent Volumes**:
   * Provides an abstraction layer for storage in the cluster, decoupling the specifics of storage provisioning from its consumption.
9. **ReplicaSets**:
   * Ensures that a specified number of Pod replicas are running at any given time for redundancy and scaling.



