# kube-clusters

Bash command for creating a kube cluster

1. Run the kube-clusters script in sudo for your controller and new workers.

   ```
   sudo ./kube-clusters.sh
   ```

3. After you've run this for all of your servers, follow these steps:

   - Run the following command on your controller:
   
     ```bash
     sudo kubeadm init --pod-network-cidr 192.168.0.0/16 --kubernetes-version 1.27.0
     ```
   
   - COPY cluster information from the above code and run it.
   
   - Run the following commands:
   
     ```bash
     kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
     kubeadm token create --print-join-command
     ```
   
   - Take your token and enter it into the worker nodes using the following command:
   
     ```bash
     sudo [kubeadm token from print-join-command]
     ```

4. View your cluster by running:
   
   ```bash
   kubectl get nodes

The final view should look like this (if the status does not say Ready, wait a few minutes and run it again):
```
cloud_user@k8s-control:~$ kubectl get nodes
NAME          STATUS   ROLES           AGE   VERSION
k8s-control   Ready    control-plane   20h   v1.24.0
k8s-worker1   Ready    <none>          20h   v1.24.0
k8s-worker2   Ready    <none>          20h   v1.24.0
```
