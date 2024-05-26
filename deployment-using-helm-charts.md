# 🚀 Deployment Using Helm Charts

## **Kubernetes Deployment (Helm Chart):**

The Helm Chart defines how the application is deployed onto a Kubernetes cluster:

* **Deployments:** Creates two separate Deployments, one for the backend and one for the frontend. Each Deployment manages the scaling (number of replicas) and updates of the respective components.
* **Services:**
  * Creates a `ClusterIP` service for the backend, accessible internally within the cluster.
  * Creates a `NodePort` service for the frontend, making it accessible outside the cluster via a specific port on each node.
  * Creates an additional `LoadBalancer` service for the frontend if needed to expose it through a cloud provider's load balancer.
* **ConfigMap:** Stores configuration values for the LLM (instruction, knowledge base, parameters), allowing easy updates without changing the application code.

## Hands-On&#x20;

On the terminal of your cluster/master node, check if you have HELM installed.

```
helm version
```

Add the k8sug-ai repository

```
helm repo add k8sug-ai https://thiago4go.github.io/charts
```

Update helm repositories

```
helm repo update
```

Search for "k8sug" on helm repos

```
helm search repo k8sug
```

<figure><img src=".gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="INSTALL" %}
You may name the **release** as you want:

```
helm install name-release k8sug-ai/k8sug-chatbot
```

<figure><img src=".gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="PULL and INSTALL" %}
If we want to change the default values we need to pull it.\
Copy the package, unzip and navigate to its folder

```
helm pull k8sug-ai/k8sug-chatbot --untar 
cd k8sug-chatbot
```

<figure><img src=".gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

We can make changes to the `values.yaml` before installing it.&#x20;

Then install it:

```
helm install test .
```

<figure><img src=".gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

That is it! You deployed the an LLM model as a Backend API , a Chatbot  as Frontend IU and the necessary services to connect them!

Lets now test it and do some exercises!
