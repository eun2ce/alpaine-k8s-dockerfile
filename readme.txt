$ docker build -t k8s-dev .

$ docker run -it \
  --privileged \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v $(pwd):/workspace \
  -v $HOME/.kube:/root/.kube \
  k8s-dev
/workspace # kind create cluster --config multi-cluster.yaml --name my-multi-cluster
Creating cluster "my-multi-cluster" ...
 ✓ Ensuring node image (kindest/node:v1.27.3) 🖼
 ✓ Preparing nodes 📦 📦 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
 ✓ Joining worker nodes 🚜
Set kubectl context to "kind-my-multi-cluster"
You can now use your cluster with:

kubectl cluster-info --context kind-my-multi-cluster

kind get kubeconfig --name my-cluster > ~/.kube/config

Thanks for using kind! 😊
/workspace # exit

$ kubectl get pods -A
NAMESPACE            NAME                                                     READY   STATUS    RESTARTS   AGE
kube-system          coredns-5d78c9869d-6w9sq                                 1/1     Running   0          31s
kube-system          coredns-5d78c9869d-ltlmc                                 1/1     Running   0          31s
kube-system          etcd-my-multi-cluster-control-plane                      1/1     Running   0          47s
kube-system          kindnet-2wbbd                                            1/1     Running   0          28s
kube-system          kindnet-pcj5s                                            1/1     Running   0          27s
kube-system          kindnet-vnl4j                                            1/1     Running   0          32s
kube-system          kube-apiserver-my-multi-cluster-control-plane            1/1     Running   0          47s
kube-system          kube-controller-manager-my-multi-cluster-control-plane   1/1     Running   0          48s
kube-system          kube-proxy-9ptb8                                         1/1     Running   0          28s
kube-system          kube-proxy-d5j8k                                         1/1     Running   0          32s
kube-system          kube-proxy-w9zl7                                         1/1     Running   0          27s
kube-system          kube-scheduler-my-multi-cluster-control-plane            1/1     Running   0          48s
local-path-storage   local-path-provisioner-6bc4bddd6b-b5ph4                  1/1     Running   0          31s
