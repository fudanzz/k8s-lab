### case-1:  docker connect to k8s private registry

1.1:  add registry certificate to local 

1.2:   docker login mycluster.icp:8500

### case-2: push image

2.1:  tag local image
docker tag registry.docker-cn.com/library/nginx:latest mycluster.icp:8500/default/nginx:latest

2.2:  push image
docker push mycluster.icp:8500/default/nginx:latest

#### case-3: access pod without service

3.1 port-forward
kubectl port-forward nginx-server 8888:80

### case-4: using labels
kubectl get po --show-labels
kubectl get po -L env,type
kubectl get po -l type=node
kubectl label po nginx-server env=test

node selector:
  nodeSelector:               1
    gpu: "true"

### case-5: isolate with namespace

kubectl create ns test

kubectl delete po --all
kubectl delete all --all

### case-6: the express way to start a pod and service

kubectl run nginx --image=nginx     ----creat a deployment

kubectl run nginx --image=nginx --dry-run -o yaml

kubectl run hellonode --image=mycluster.icp:8500/default/hello-node --generator=run/v1

kubectl expose rc hellonode --type NodePort --port 80 --target-port=8000