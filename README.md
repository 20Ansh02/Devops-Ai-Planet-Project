
<div align="center">

  <h1>ArgoCD for Continuous Deployment</h1>
  
  <p>
    Argo CD for continuous deployment and Argo Rollouts for advanced deployment strategies within a Kubernetes environment! 
  </p>
  
<br />
</div>
<!-- Table of Contents -->
# :notebook_with_decorative_cover: Table of Contents

- About the Project
- [Getting Started](#toolbox-getting-started)
  * [Prerequisites](#bangbang-prerequisites)
  * [Steps](#gear-installation)
- [License](#warning-license)

  

<!-- About the Project -->
## :star2: About the Project
Hands-on experience with GitOps practices, utilizing Argo CD for continuous deployment and Argo Rollouts for advanced deployment strategies within a Kubernetes environment. You will be responsible for setting up a GitOps pipeline that automates the deployment and management of a simple web application.

The tasks involve setting up a GitOps pipeline using Argo CD and Argo Rollouts on a Kubernetes cluster. <br>
In Task 1, a GitHub repository is created to host the source code, and Argo CD is installed and configured on the cluster. Additionally, Argo Rollouts controller is installed to manage progressive delivery.<br>
Task 2 focuses on creating the GitOps pipeline by Dockerizing the chosen web application, pushing the Docker image to a public registry, and configuring Argo CD to automatically deploy changes to the Kubernetes cluster based on the repository changes. <br>
Finally, Task 3 implements a canary release strategy using Argo Rollouts by defining rollout strategies, triggering a rollout with updated Docker images, and monitoring the deployment process to ensure the success of the canary release.<br>
### ArgoCD

  ![download](https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/8cb8b8cc-a1de-43c4-96ba-a8f455cabb97)

Argo CD is a Kubernetes-native, open-source, continuous delivery (CD) tool that uses Git repositories to define application states and automate their deployment. Argo CD can manage both infrastructure configuration and application updates in one system.

### Docker

![images](https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/00c8c3ab-2dc9-4ebf-b318-3e9653c46a69)

Docker revolutionized software development by popularizing containerization, a lightweight and efficient way to package applications and their dependencies. With Docker, developers can encapsulate their applications and run them consistently across different environments, from development to production. Docker containers provide isolation, ensuring that applications run predictably regardless of the environment they are deployed. Docker's ease of use, portability, and scalability have made it a cornerstone technology in modern software development and deployment pipelines. Its impact extends beyond development, influencing practices like microservices architecture, continuous integration and deployment (CI/CD), and DevOps. As a result, Docker has become an essential tool for developers, enabling them to build, ship, and run applications more efficiently and reliably.

### Kubernetes

![3-31510_svg-kubernetes-logo-hd-png-download](https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/42bae3fd-a414-40da-94ef-d114c93505d4)

Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications. Originally developed by Google and now maintained by the Cloud Native Computing Foundation (CNCF), Kubernetes has become the de facto standard for managing containerized workloads in cloud-native environments. Kubernetes abstracts away the underlying infrastructure, providing a unified API to manage clusters of hosts and the containers running on them. It offers features such as automatic scaling, rolling updates, service discovery, load balancing, and self-healing capabilities, enabling developers to focus on building applications without worrying about the underlying infrastructure complexities. Kubernetes promotes scalability, resilience, and portability, allowing applications to run consistently across diverse environments, from on-premises data centers to public and hybrid clouds. Its rich ecosystem of tools and integrations, combined with its flexibility and robustness, makes Kubernetes indispensable for modern containerized application development and deployment.

<!-- TechStack -->
### :space_invader: Tech Stack

<details>
<summary>DevOps</summary>
  <ul>
    <li><a href="https://www.docker.com/">Docker</a></li>
    <li><a href="https://www.kubernetes.com/">Kubernetes</a></li>
    <li><a href="https://argocd.com/">Argocd</a></li>
  </ul>
</details>


<!-- Getting Started -->
## 	:toolbox: Getting Started

<!-- Prerequisites -->
### :bangbang: Prerequisites

This project uses Docker.<br>
So one should have basic knowledge Docker

<a href="https://www.docs.docker.com/">Docker Dcumentation</a>

This project uses ArgoCD.<br>
So one should have basic knowledge ArgoCD

<a href="https://argo-cd.readthedocs.io/">ArgoCD Dcumentation</a>

This project uses Kubernetes.<br>
So one should have basic knowledge Kubernetes

<a href="https://kubernetes.io/docs/home/">Kubernetes Dcumentation</a>

<!-- Prerequisites -->
### :bangbang: System Requirements


```
- 2 CPUs or more
- 2 GB of free memory
- 20 GB of free disk space
- Internet connection

NOTE : "t3.large" perfect suit for this lab
```
<!-- Installation -->
### :gear: Installation

Install Docker

```
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
$ ls -l /var/run/docker.sock
$ id
$ sudo usermod -aG docker $USER && newgrp docker
$ id
$ docker --version
```
Install Kubctl

```
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl &&   chmod +x ./kubectl && sudo mv ./kubectl /usr/local/bin/kubectl
$ sudo chmod +x /usr/local/bin/kubectl
$ ls -l /usr/local/bin/kubectl
$ kubectl version --short
```
Install Minikube

```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
$ ls -l 
$ sudo install minikube-linux-amd64 /usr/local/bin/minikube
$ minikube version
```


   
<!-- Running Tests -->
# :test_tube: Running Project

To execute project, Run the following commands in order

# ⚙️Task 1:Setup and Configuration

### 🔹STEP-1
#### Launching EC2 instance

By following <a href="https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwjE3qv-seCFAxXcpmYCHT5rCi0YABAAGgJzbQ&ase=2&gclid=CjwKCAjwoa2xBhACEiwA1sb1BE6UP7kdZ4en8_8FPqL-4W7HW8FslTOwYsaJ5junmX7V2-QxRPkh8BoCPysQAvD_BwE&ei=beIrZo6lN6mq4-EP58-K0AY&ohost=www.google.com&cid=CAESVuD2IYlLONq6IAQ-4HSBs-GyUSz3w7NUmsk066zXi43zLoikHGwMqYxHXZjARUM8F6fsb297cLgolY8X2kIgdhnzu7KBhRpD45QBwj3q4Z0kpgThkkWM&sig=AOD64_0FvAkaIQibFEy5SM4IHiqqz1oA5A&q&sqi=2&nis=4&adurl&ved=2ahUKEwjOj6b-seCFAxUp1TgGHeenAmoQ0Qx6BAgOEAE">AWS Documentation</a> Create and Launch EC2 instance.


<br/>

### 🔹STEP-2
#### Update Ubuntu packages install required package for this lab
```
$ sudo apt-get update -y
$ sudo apt-get install apt-transport-https curl conntrack
```

<br/>

### 🔹STEP-3
#### Install Docker
```
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
$ ls -l /var/run/docker.sock
$ id
$ sudo usermod -aG docker $USER && newgrp docker
$ id
$ docker --version
```

<br/>

### 🔹STEP-4
#### Install Kubectl
```
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl &&   chmod +x ./kubectl && sudo mv ./kubectl /usr/local/bin/kubectl
$ sudo chmod +x /usr/local/bin/kubectl
$ ls -l /usr/local/bin/kubectl
$ kubectl version --short
```

<br/>

### 🔹STEP-5
#### Install Minikube
```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
$ ls -l 
$ sudo install minikube-linux-amd64 /usr/local/bin/minikube
$ minikube version
```

<br/>

### 🔹STEP-6
#### Start Minikube
```
$ kubectl cluster-info
$ minikube start
$ kubectl cluster-info
```

<br/>

### 🔹STEP-7
#### Check Minikube status
```
$ minikube status
$ kubectl get nodes
```

<br/>

### 🔹STEP-8
#### Download ArgoCD
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

<br/>

### 🔹STEP-9
#### Check all ArgoCD resources are up and running.

```
kubectl get all -n argocd

```

<br/>

### 🔹STEP-10
#### Extracting Password Of ArgoCD

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

<br/>

### 🔹STEP-11
#### Forwarding Port from 8000 to 443

```
kubectl port-forward svc/ardocd-server -n argocd --address 0.0.0.0 8080:443
```

<br/>


### 🔹STEP-12
#### Login to ArgoCD

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

<br/>

### 🔹STEP-13
#### Installing ArgoCD Rollouts

```
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
brew install argoproj/tap/kubectl-argo-rollouts

```

<br/>

# ⚙️ Task 2: Creating GITOPS Pipeline

### 🔹STEP-1
 #### Dockerize the application
👉Created sample node js webapp v1
👉Create production grade Dockerfile
👉Added github actions to build docker image and push to docker hub located at lulad7/ai-planet-demo
👉github actions workflow file located at .github/workflows/main.yml

<br/>

### 🔹STEP-2
#### Deploy the application using ArgoCD

```
kubectl create ns ai-planet-demo
```
### 🔹STEP-3
Created Deployment.yaml and Service.yaml - NodePort inside deployment folder

### 🔹STEP-4 
Change default admin password

```
argocd account update-password
```
### 🔹STEP-5
Created a project on argocd named ai-planet-demo 

### 🔹STEP-6
Added <a href="https://github.com/20Ansh02/Devops-Ai-Planet-Project"> as a scoped repository inside the project

### 🔹STEP-7
Created and connected the Repository

### 🔹STEP-8
Added the application ai-planet-demo to the project Ai-Planet-Peoject
![image](https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/ac39d73b-f7e4-46e4-8a2d-dbcd0cbb504b)


<br/>

# ⚙️ Task 3: Implementing a Canary Release with Argo Rollouts

### 🔹STEP-1 First Rollout
👉 Changed from Deployment type to Rollout
👉 Added canary strategy to deployment file with 1 minute interval between each step
```
strategy:
        canary:
        steps:
        - setWeight: 20
        - pause: {}
        - setWeight: 40
        - pause: {duration: 1}
        - setWeight: 60
        - pause: {duration: 1} 
```
👉 Using exisiting version for first deployment ai-planet-demo:1.2
👉 Push to repository to main branch and trigger github actions
👉 At the same time Wait for argocd to detect the change in manifest files and redeploy the rollout

<img width="1181" alt="3 1argo-final" src="https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/d17cb38c-d60f-429c-92a9-8014e4c1a3f4">

👉 Run command to inspect rollout
```
kubectl argo rollouts get rollout ai-planet-demo-rollout -n ai-planet-demo --watch
```
<img width="1284" alt="3 1argo-ai-final" src="https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/3332c497-459e-4138-9a68-81cf3465c3cd">

👉 Rollout successfully deployed for first time without waiting or approval from operator

<br/>

### 🔹STEP-2 Second Rollout

👉 Make modification to we app change to AI Planet Version 2
👉 Change Github actions file to build image version ai-planet-demo:1.3
👉 Modify Rollout Deployment file to use image version ai-planet-demo:1.3
👉 Push repository to main branch and trigger github actions automatically

<img width="1455" alt="action-final" src="https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/d64c8c13-7674-4858-990e-04f8a8ebafef">
👉 At the same time Wait for argocd to detect the change in manifest files and deploy revision2 of the rollout automatically

<img width="1229" alt="3 2argo-ai-middle" src="https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/e6145844-72ef-46b8-9d50-f9c8490ba6af">

### 🔹STEP-1 Second Rollout

👉 Monitor the Rollout

```
kubectl argo rollouts get rollout ai-planet-demo-rollout -n ai-planet-demo --watch
```

👉 First only set to 20% trafic and waits for operator approval

👉 Approve and promote the rollout
```
kubectl argo rollouts promote ai-planet-demo-rollout -n ai-planet-demo
```
👉 then: 40% -> 1 minute pause -> 60% -> 1 minute pause -> 100% rollout

<img width="1340" alt="argo-final-final" src="https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/4fdec682-1cd8-4fbf-a1e1-73662a7f81ef">

<br/>

# ⚙️ Task 4: Document and Cleanup

👉 Documentation Comleted alongside working on project

### 🔹STEP-1 Clean Up

👉 Documentation Comleted alongside working on project

👉 Delete the application and project from ArgoCD

```
Run command to uninstall argo rollouts and delete namespace

kubectl delete -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

kubectl delete ns argo-rollouts
```
👉 Run command to uninstall argo rollout plugin brew uninstall argoproj/tap/kubectl-argo-rollouts

👉 Run command to uninstall ArgoCD and delete namespace
```
kubectl delete -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl delete ns argocd
```
👉 Run command to delete ai-planet-demo namespace
```
kubectl delete ns ai-planet-demo
```
👉 Run command to delete minikube cluster profile
```
minikube delete
```
👉 Follow recommended procedures to disable Github Actions and Delete repository if required




<!-- Challenges -->
### Challenges Faced

#### Challenge 1:
👉 Facing issue regarding Port Forwarding
was showing this error
![WhatsApp Image 2024-04-23 at 17 33 22_82af64cf](https://github.com/20Ansh02/Devops-Ai-Planet-Project/assets/83866039/1a4f6bbf-edf5-4866-8535-b0b27b035135)

👉 Solved using 
```
kubectl port-forward svc/ardocd-server -n argocd --address 0.0.0.0 8080:443
```

#### Challenge 2:
 👉 Unable to run amd64 version on mac m2 requiring arm64 image
 👉 Fix:- added platform: arm64 to github actions main.yml file on build and push docker image step
 

Contributions are always welcome!
