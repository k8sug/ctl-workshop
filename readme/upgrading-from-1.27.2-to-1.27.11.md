---
description: play with kubernetes
---

# Upgrading from 1.27.2 to 1.27.11

## We will practice with hands-on labs!



{% code overflow="wrap" %}
```
yum-config-manager --save --setopt=kubernetes.skip_if_unavailable=true
```
{% endcode %}

{% code overflow="wrap" %}
```
kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
```
{% endcode %}

```
export KUBECONFIG=/etc/kubernetes/admin.conf
  
```

{% code overflow="wrap" %}
```
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```
{% endcode %}

```
cat <<EOF | tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.27/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.27/rpm/repodata/repomd.xml.key
exclude=kubelet kubeadm kubectl
EOF
```

```
yum list --showduplicates kubeadm --disableexcludes=kubernetes
```

1. Upgrade kubeadm:

{% tabs %}
{% tab title="Ubuntu, Debian" %}
```bash
# replace x in 1.27.x-* with the latest patch version
apt-mark unhold kubeadm && \
apt-get update && apt-get install -y kubeadm='1.27.x-*' && \
apt-mark hold kubeadm
```
{% endtab %}

{% tab title="CentOS" %}
```bash
# replace x in 1.27.x-* with the latest patch version
yum install -y kubeadm-'1.27.x-*' --disableexcludes=kubernetes
```
{% endtab %}
{% endtabs %}

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><strong>yum install -y kubeadm-'1.27.11-150500.1.1' --disableexcludes=kubernetes
</strong></code></pre>

1.  Verify that the download works and has the expected version:

    ```shell
    kubeadm version
    ```
2.  Verify the upgrade plan:

    ```shell
    kubeadm upgrade plan
    ```

```
kubeadm upgrade apply v1.27.11
```

#### Drain the node <a href="#drain-the-node" id="drain-the-node"></a>

Prepare the node for maintenance by marking it unschedulable and evicting the workloads:

```shell
# replace <node-to-drain> with the name of your node you are draining
kubectl drain node1 --ignore-daemonsets
```





```
yum install -y kubelet-'1.27.11-150500.1.1' kubectl-'1.27.11-150500.1.1' --disableexcludes=kubernetes

```



