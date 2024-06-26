# 🚀 Deployment Using Helm Charts

## What is helm? <a href="#what-is-helm" id="what-is-helm"></a>

Helm is often referred to as the 'app store' for Kubernetes, offering a powerful and flexible way to manage Kubernetes applications. Helm Charts help you define, install, and upgrade even the most complex Kubernetes application, streamlining the deployment process.

## **Application Deployment (Helm Chart):**

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
{% tab title="PULL and INSTALL" %}
We may want to change the default values, so we need to pull it.\
Copy the package, unzip and navigate to its folder

```
helm pull k8sug-ai/k8sug-chatbot --untar 
cd k8sug-chatbot
```

<figure><img src=".gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

We can make changes to the `values.yaml` before installing it.&#x20;

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>Using an Editor on Killercoda</p></figcaption></figure>

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>Using VI/VIM</p></figcaption></figure>

Then install it:

```
helm install test .
```

<figure><img src=".gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Just Install" %}
You may name the **release** as you want:

```
helm install name-release k8sug-ai/k8sug-chatbot
```

<figure><img src=".gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

That is it!&#x20;

You've successfully deployed the LLM model as a Backend API that utilizes variables from a ConfigMap, along with a chat interface as the Frontend UI. Additionally, you've set up all the necessary services to link these components together!

```
kubectl get all,configmap 
```

<figure><img src=".gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

Lets now test it and do some exercises!
