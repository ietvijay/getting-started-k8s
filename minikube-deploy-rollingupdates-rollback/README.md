A. Deploy the Pods using Deployment object and update the pods using rolling updates , then rollback to previus version
//We will use minikube for this

1. Open a new terminal window:
  > minikube.exe start
2. Run the nodeport service.
  > kubectl.exe  apply -f ./svc-nodeport.yml
3.	Port Forwarding on the service from minikube
  > minikube.exe service ps-nodeport
4. Deploy version v1 of the hello-world-web app
	> kubectl.exe  apply -f ./deploy-v1.yml
5. Check the status of rollout
	> kubectl.exe rollout status deploy web-deploy
6. Test the app using localhost:<minikube forward port>  in step 3.

-- Rollingupdate: Update the app from version v1 to v2 using 
7.  Deploy the app using deployment
	> kubectl apply -f ./deploy-rollingupdate-v2.yml
8. Check the status of rollout
	> kubectl.exe rollout status deploy web-deploy
9. Refresh the browers to see the updated app.

- Check the old and new RS
	>kubectl.exe get rs
- Verify the image in the old RS 
	> kubectl.exe describe web-deploy-7cbc7cc48f

--Rollback
10. Let check the rollout history 
	> kubectl.exe rollout history deploy web-deploy
11. Rollback to a version
	> kubectl.exe rollout undo deploy web-deploy --to-revision=1
12. Refresh the browser to check the rollback is complete