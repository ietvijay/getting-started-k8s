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
    > eksctl create cluster --name eks-lab1-cluster --region us-east-1 --fargate
3. Create Pod yml
    > kubectl.exe apply -f .\pod.yml
4. Check pods
    > Kubectl get pods --watch
5. Describe pod created:
    > kubectl.exe  describe pod my-app
6. Run to exec into the container.
    > kubectl exec -i -t my-app --container web-app -- /bin/sh
