# kube-clusters
Bash command for creating kube klusters

Run this script in sudo for your controller and new workers

After you ran this for all of your servers run the following:

sudo kubeadm init --pod-network-cidr 192.168.0.0/16 --kubernetes-version 1.27.0
COPY cluster information from above code and run it
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
kubeadm token create --print-join-command

***Take your token and enter "sudo ---kubeadm token from print-join-command into the workers--- ***

View your cluster by running "kubectl get nodes"


Final view should look like this (if the status does not say Ready wait a few minuets and run it again)
cloud_user@k8s-control:~$ kubectl get nodes
NAME          STATUS   ROLES           AGE   VERSION
k8s-control   Ready    control-plane   20h   v1.24.0
k8s-worker1   Ready    <none>          20h   v1.24.0
k8s-worker2   Ready    <none>          20h   v1.24.0
