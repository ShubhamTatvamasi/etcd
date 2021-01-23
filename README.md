# etcd

Install etcd
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
kubectl create namespace etcd

helm install etcd bitnami/etcd \
  -n etcd
```


