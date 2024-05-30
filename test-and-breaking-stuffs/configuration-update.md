---
description: 'Objective: Update application configuration using ConfigMaps.'
---

# ⬆️ Configuration Update

### First, lets check the pod logs

Copy  the pod name from the UI

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

```
kubectl logs <podname> | grep -v "GET /health"
```

You may see an error:

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

### Using Helm to update values:

Locate and edit the values.yaml&#x20;

If you did not pull the Chart while installing, you can get the values using:

```
helm show values k8sug-ai/k8sug-chatbot > values.yaml
```

Once saved, upgrade using this command:

```
helm upgrade <release-name> k8sug-ai/k8sug-chatbot --values ./values.yaml
```

**Pros:**

1. **Consistency:** Ensures that the cluster state remains consistent with the desired state defined in the Helm chart, making it easier to manage and reproduce environments.
2. **Version Control:** Changes are tracked and versioned, allowing for better management and rollback capabilities.
3. **Automation:** Helm upgrades automate the process of applying changes, reducing the risk of human error.
4. **Idempotency:** Helm ensures that applying the same chart repeatedly will not alter the state of the cluster if there are no changes, maintaining idempotency.

**Cons:**

1. **Learning Curve:** Requires understanding of Helm and its templating system, which might be an additional overhead for newcomers.
2. **Delayed Changes:** Changes require updating the chart and running the Helm upgrade command, which might be slightly slower than direct edits.



### Editing the k8s object directly

```
kubectl edit configmap chatbot-config
```

**Pros:**

1. **Immediate Changes:** Changes are applied immediately to the running cluster without the need for additional commands.
2. **Flexibility:** Allows for quick adjustments and experimentation.

**Cons:**

1. **State Drift:** Direct modifications can cause the state of the cluster to drift away from the desired state defined in the Helm chart, making it harder to manage and reproduce the environment.
2. **Manual Effort:** Requires manual tracking of changes, which can be error-prone and difficult to manage, especially in larger environments.
3. **Inconsistent States:** If changes are not documented or replicated in the Helm chart, future Helm upgrades might overwrite these modifications, leading to inconsistencies.

