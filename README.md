# etcd

Install etcd
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
kubectl create namespace etcd

helm install etcd bitnami/etcd \
  -n etcd \
  --set persistence.storageClass=manual \
  --set persistence.size=1Gi
```

Run the follwoing command on the node for giving volume permission to the pod:
```bash
chown 1001:1001 /opt/etcd
```

Setup volume
```bash
kubectl apply -f - << EOF
apiVersion: v1
kind: PersistentVolume
metadata:
  name: etcd
spec:
  storageClassName: manual
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 1Gi
  hostPath:
    path: "/opt/etcd"
EOF
```

