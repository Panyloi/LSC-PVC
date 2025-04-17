# LSC-PVC
Yaml files and description for NFS server and provisioner

### How to run
1. Create `EKS` cluster with 2 nodes (enable TCP traffic in the security group)
2. Run `helm` commands  
    ```helm repo add nfs-ganesha-server-and-external-provisioner https://kubernetes-sigs.github.io/nfs-ganesha-server-and-external-provisioner/
    helm repo update
    helm install my-nfs nfs-ganesha-server-and-external-provisioner/nfs-server-provisioner
    ```
3. Apply `yaml` files
    ```
    kubectl apply -f pvc.yaml
    kubectl apply -f nginx-deployment.yaml
    kubectl apply -f nginx-service.yaml
    kubectl apply -f populate-job.yaml
    ```

4. Get Node IP and check website
    ```
    kubectl get svc nginx-service
    ```

### Description of commands
`helm` provides image for nfs server and provisioners. By adding chart from repo we can get to it and install it on the cluster.
`kubectl apply` deploys yaml files with description of the kind of deployment
`kubectl get svc nginx-service` will get IP required for checking the website on provided IP