# Using Helm Charts

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
