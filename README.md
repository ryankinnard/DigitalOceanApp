## Todo App Deployment Guide
### This guide provides step-by-step instructions to deploy the Todo App\

Prerequisites

	1.	A DigitalOcean account.
	2.	DigitalOcean Kubernetes cluster set up.
	3.	kubectl installed and configured to connect to your DigitalOcean cluster.
	4.	doctl installed and authenticated with your DigitalOcean account.
	5.	Docker installed for building and pushing container images.
 	6.	Managed MySQL database created on DigitalOcean and K8s cluster added as trusted source


1. Clone the Repository

2. Create Docker Image<br/> 
```docker build -t todo-app .```

3. Create a DigitalOcean Container Registry if you have not done so already<br/>
   ```doctl registry create <your-registry-name>```

4. Tag Docker Image<br/>
```docker tag todo-app registry.digitalocean.com/<your-registry-name>/todo-app```

5. Push image to registry<br/>
```docker push registry.digitalocean.com/<your-registry-name>/todo-app```

6. Create running container<br/>
   ```docker run -p 3000:5000 registry.digitalocean.com/<your-registry-name>/todo-app```
7. Create a Kubernetes Secret for the Database<br/>
   ```kubectl create secret generic db-credentials --from-literal=DATABASE_URI="mysql://<username>:<password>@<host>:<port>/<database>```
8. Deploy Application<br/>
   ```kubectl apply -f deployment.yaml```
9. Expose Application<br/>
    ```kubectl apply -f service.yaml```
10. Enable Horizontal Pod Autoscaling<br/>
    ```kubectl apply -f hpa.yaml>```
