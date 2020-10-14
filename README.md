# minkube
Kuberenetes &amp; Docker tools and scripts

kubeadm --apiserver-advertise-address 192.168.1.221 --control-plane-endpoint 192.168.1.221 init
kubeadm --apiserver-advertise-address 192.168.1.221 init

Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.1.221:6443 --token 4zhlk8.uq688xuump0t3u44 \
    --discovery-token-ca-cert-hash sha256:9e27b013402de2b5d08fc8fc6a251f9518034389648a76cb6cca5e26f5c988d2 



vagrant@ct-r2py ~]$ kubectl cluster-info
Kubernetes master is running at https://10.0.2.15:6443
KubeDNS is running at https://10.0.2.15:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.


[vagrant@ct-r2py ~]$ kubectl get nodes
NAME      STATUS     ROLES    AGE   VERSION
ct-r2py   NotReady   master   22m   v1.18.3


kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"

kubectl get pods --all-namespaces
NAMESPACE     NAME                              READY   STATUS    RESTARTS   AGE
kube-system   coredns-66bff467f8-9x2k5          1/1     Running   0          84m
kube-system   coredns-66bff467f8-xbw4m          1/1     Running   0          84m
kube-system   etcd-ct-r2py                      1/1     Running   0          84m
kube-system   kube-apiserver-ct-r2py            1/1     Running   0          84m
kube-system   kube-controller-manager-ct-r2py   1/1     Running   0          84m
kube-system   kube-proxy-bh2jr                  1/1     Running   0          84m
kube-system   kube-scheduler-ct-r2py            1/1     Running   0          84m
kube-system   weave-net-zgsgv                   2/2     Running   0          32m


