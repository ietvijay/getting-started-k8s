A. Bulild and Upload a hello-worl app docker image to Docker Hub repo.

1. Build the image:
    > docker build -t hello-world-web:v1 .
2. Login to Docker hub:
    > docker login --username=yourhubusername --email=youremail@company.com
3. List the images:
    > docker images

4. Tag your image:
    > docker tag <Image ID> <yourhubusername>/<app name>:<version>
5. Push the image to Docker Hub:
    > docker push yourhubusername/<app name>:<version>


B. Lets create a Kubernetes Cluster in AWS
1. Install kubectl and eksctl using Chocolatey:
    >choco install kubernetes-cli 
    >choco install -y eksctl

2. Create cluster using eksctl:
    > eksctl create cluster --name eks-ec2lab-clusters --region us-east-1 --with-oidc --ssh-access --ssh-public-key vijaykvp2 --managed
3. Create Pod yml
    > kubectl.exe apply -f .\pod.yml
4. Check pods
    > Kubectl get pods --watch
5. Describe pod created:
    > kubectl.exe  describe pod my-app
6. Create NodePort 
    > kubectl.exe apply -f .\svc-nodeport.yml
7.  Get and Describe Nodeport
    > kubectl.exe get svc
    > kubectl.exe describe svc ps-nodeport
    
8. Create lb
    > kubectl.exe apply -f .\svc-lb.yml
9. Get public add of lb
    >  kubectl.exe get svc
8. Use aa7a9ddab1d874bdfaf1d5a79674048d-183294484.us-east-1.elb.amazonaws.com dns to load the hello world app from internet 



-- Clean up

1. Delete pods
>  kubectl.exe delete -f .\pod.yml
2. Delete nodeport
> kubectl.exe delete -f .\svc-nodeport.yml
3. Delete lb
>  kubectl.exe delete -f .\svc-lb.yml
4. Delete cluster
> eksctl delete cluster --name eks-ec2lab-clusters