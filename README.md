# k8s-kubeadm-openstack
Install K8s with kubeadm on OpenStack


## RHEL only:

```
subscription-manager register
subscription-manager attach && \
  subscription-manager repos --enable=rhel-7-server-extras-rpms
```

##

```
echo "$(/sbin/ifconfig eth0 | grep 'inet ' | awk '{print $2}') $(hostname)" >> /etc/hosts

yum install -y git && \
  git clone https://github.com/rvanbutselaar/k8s-kubeadm-openstack.git && \
  cd k8s-kubeadm-openstack

./prepare.sh
```

## Delete

```
kubeadm reset
iptables -F && iptables -t nat -F && iptables -t mangle -F && iptables -X
rm -rf ~/.kube/
```
