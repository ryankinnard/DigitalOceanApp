# DigitalOceanApp

Todo App Deployment Guide\
This guide provides step-by-step instructions to deploy the Todo App.


Prerequisites

	1.	A DigitalOcean account.
	2.	DigitalOcean Kubernetes cluster set up.
	3.	kubectl installed and configured to connect to your DigitalOcean cluster.
	4.	doctl installed and authenticated with your DigitalOcean account.
	5.	Docker installed for building and pushing container images.

1. Clone the Repository

2. Create Docker Image 
docker build -t todo-app .

3. Upload Docker Image
   Create a DigitalOcean Container Registry if you have not done so already
   	doctl registry create <your-registry-name>


   
   

