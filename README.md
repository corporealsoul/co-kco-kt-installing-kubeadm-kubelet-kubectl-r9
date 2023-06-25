### KUBEADM , KUBELET and KUBECTL

**Installing kubeadm, kubelet and kubectl , Red Hat 9 ,** https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/#installing-kubeadm-kubelet-and-kubectl

    [anup@rhel-92-04 ~]$ cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
    [kubernetes]
    name=Kubernetes
    baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
    enabled=1
    gpgcheck=1
    gpgkey=https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
    exclude=kubelet kubeadm kubectl
    EOF

`[anup@rhel-92-04 ~]$ cat /etc/yum.repos.d/kubernetes.repo`

`[anup@rhel-92-04 ~]$ sudo setenforce 0`

`[anup@rhel-92-04 ~]$ sudo sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config`

`[anup@rhel-92-04 ~]$ sudo yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes`

`[anup@rhel-92-04 ~]$ sudo systemctl enable --now kubelet`

<br>

`[anup@rhel-92-04 ~]$ kubelet --version`

`[anup@rhel-92-04 ~]$ kubeadm version`

`[anup@rhel-92-04 ~]$ kubectl version`

`[anup@rhel-92-04 ~]$ kubectl version --client`

`[anup@rhel-92-04 ~]$ kubectl cluster-info`

`[anup@rhel-92-04 ~]$ kubectl version -o json`

<br>
