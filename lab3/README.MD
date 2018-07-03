### case-1:  configMap





### case-1:  secret




notes:

config app by passing parameters

1, passing command-line arguments to container

RENTRYPOINT
CMD

docker run <image>  <arguments>

Overriding the command and arguments in Kubernetes
kind: Pod
spec:
  containers:
  - image: some/image
    command: ["/bin/command"]
    args: ["arg1", "arg2", "arg3"]

2, Setting environment variables for a container 


kind: Pod
spec:
 containers:
 - image: luksa/fortune:env
   env:                            
   - name: INTERVAL                
     value: "30"
     
3, decoupd configuration from pod spec by using configmap



4, store sensitive data in secret 
