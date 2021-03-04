1. Run the Mongo db
    > kubectl apply -f ./mongo-deployment.yml
    > kubectl logs -f deployment/mongo

2. Run the service for mongo db
    > kubectl apply -f ./mongo-service.yml
3. Check the pods
    > kubectl get pods
4. Run the frontend app
    > kubectl apply -f ./frontend-deployment.yml
5. Run the frontend service
    > kubectl apply -f ./frontend-service.yml
6. Port-forward the FrontEnd service to access from local browser   
    > kubectl port-forward svc/frontend 8080:80
7. test on localhost:8080

8. Scale Up the frontend app
 > kubectl scale deployment frontend --replicas=5
 > kubectl get pods
9. Sclare down the frontend App
  >kubectl scale deployment frontend --replicas=2
  > kubectl get pods

10. Clean up
    > kubectl.exe delete deployment,service -l app.kubernetes.io/name=mongo
    > kubectl.exe delete deployment,service -l app.kubernetes.io/name=guestbook
    > kubectl.exe get pods