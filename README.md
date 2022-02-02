# kubernetes-certificate-renewal-guide

Kubernetes Certificate Renewal

Check Certificate validity:
Kubeadm certs check-expiration (for v20 or greater)

Kubeadm alpha certs check-expiration (for k8s v18 or less)

If expired then run following commands:
mkdir -p $HOME/k8s-old-certs/pki
sudo cp -p /etc/kubernetes/pki/*.* $HOME/k8s-old-certs/pki
ls $HOME/k8s-old-certs/pki
sudo cp -p /etc/kubernetes/*.conf $HOME/k8s-old-certs
sudo cp -r /etc/kubernetes/pki/etcd/ $HOME/k8s-old-certs/pki
ls -ltr $HOME/k8s-old-certs
mkdir -p $HOME/k8s-old-certs/.kube
sudo cp -p ~/.kube/config $HOME/k8s-old-certs/.kube/.
ls -l $HOME/k8s-old-certs/.kube/.

kubeadm alpha certs renew all (for k8s v18 or less)
kubeadm certs renew all (for v20 or greater)

kubeadm alpha certs check-expiration
systemctl daemon-reload && systemctl restart kubelet.service




TRY THIS:
cp -r .kube/ .kube_bak
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

kubectl get nodes
   
                        OR

Move Static pods for 20-30 seconds
mkdir $HOME/staticpod
mv /etc/kubernetes/manifest/* $HOME/staticpod/


Now move back to /etc/kubernetes/manifest/
mv $HOME/staticpod/* /etc/kubernetes/manifest/

Confirm the kubelet services are running and communication between the worker nodes and the Kubernetes master is working.
kubectl get nodes
