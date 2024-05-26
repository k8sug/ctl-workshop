# 🎡 Getting a Cluster Ready

## Options Available:

### [1 - Azure (30 days free trial)](getting-a-cluster-ready.md#id-1-azure)

It is free for 30 days for new accounts, but a valid Credit or Debit card number is required.\
Great environment and quite resouceful VMs.

### [2 - Killercoda - Kubernetes Playgroud (free version available)](getting-a-cluster-ready.md#id-2-killercoda)

It is totally free, with the limitation to 60 minutes sessions. Also it is quite limited on resources. max of 4GB of RAM and only one Node. Pros: have the latest version of the most used applications and Kubernetes 1.30

### [3 - Play-with-k8s (free to use with some limitations)](getting-a-cluster-ready.md#id-3-play-with-kubernetes)

Also totally free, with limitaion to 4 hours per session. It make avaible up to 5 nodes of 4GB of RAM. Good enviroment for learning. Cons: there is an issue not make the cluster accessible from outside.



## 1: Azure

{% embed url="https://azure.microsoft.com/en-us/free" %}

<figure><img src=".gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

User a existing Microsoft/Hotmail/Skype/Github account or create a new one.

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

After signup you will be redirect to portal.azure.com

{% embed url="https://portal.azure.com/#home" %}

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

You will be given an important choice: Bash or PowerShell

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption><p>Go with Bash</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Select the Azure Subscription and click in Apply, it will give you a terminal.\


<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption><p>Switch to Bash if you have select PowerShell</p></figcaption></figure>

```
// Copy this repository
git clone https://github.com/yongkanghe/aks-casa.git;cd aks-casa
```

```
// Automation to spin-up a cluster
./aks-deploy.sh
```

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

## 2: Killercoda

{% embed url="https://killercoda.com/playgrounds/course/kubernetes-playgrounds/one-node-4GB" %}

Sign-in using a Github, Gitlab, Google or Email.

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

It will provide a Node with 4gb.

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

You can click and reduce the slide menu.&#x20;

<figure><img src=".gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

And if you click in Editor, it will provide an VSCode like enviroment.

<figure><img src=".gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

## 3: Play-With-Kubernetes



{% embed url="https://labs.play-with-k8s.com/" %}

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption><p>Play with Kubernetes</p></figcaption></figure>

{% hint style="info" %}
Login with a Docker Hub or Github account
{% endhint %}

<figure><img src=".gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Click in "Start."</p></figcaption></figure>

It will give you free access to the lab for 4 hours!

<figure><img src=".gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Click in this icon to get some setting options

<img src=".gitbook/assets/image (5) (1).png" alt="" data-size="original"><img src=".gitbook/assets/image (6) (1).png" alt="" data-size="original">
{% endhint %}

### Setting up the Control Plane

Click in "Add New Instance", it will start a VM, follow the instructions on the screen

<figure><img src=".gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

#### 1- Initializes cluster master node:

<pre data-overflow="wrap"><code><strong>kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
</strong></code></pre>

Once the initialization is completed, execute the following:

```
export KUBECONFIG=/etc/kubernetes/admin.conf
```

<figure><img src=".gitbook/assets/image (8) (1).png" alt=""><figcaption><p>Save it for later</p></figcaption></figure>

#### 2- Initialise cluster networking:

{% code overflow="wrap" %}
```
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```
{% endcode %}

{% hint style="info" %}
Kubernetes do not provides networking out of the box.
{% endhint %}

### Adding Worker Nodes

<figure><img src=".gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```
// Paste the command from the previous step
// this is sample:
kubeadm join 192.168.0.18:6443 --token xn5b6e.f4m7zofss5zqcc21 \
        --discovery-token-ca-cert-hash sha256:043642c457c553b8a692b3d45e34f0b9e5e158722180a3444e1b5990f2043647
```
{% endcode %}



This Lab allow us to have up to 5 nodes

Check the nodes using the following command  on the Master Node, aka Control Plane:

```
kubectl get nodes
```

<figure><img src=".gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

