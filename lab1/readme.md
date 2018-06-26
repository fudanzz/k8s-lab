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

