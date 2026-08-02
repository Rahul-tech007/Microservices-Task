\# Kubernetes Microservices Deployment



\## Project Overview



This project demonstrates the deployment of a containerized Node.js microservices application on Kubernetes using Minikube.



The application consists of four microservices:



| Service | Port | Description |

|----------|------|-------------|

| User Service | 3000 | Returns user information |

| Product Service | 3001 | Returns product information |

| Order Service | 3002 | Creates and retrieves orders |

| Gateway Service | 3003 | API Gateway for all backend services |



\---



\# Project Structure



```

Microservices/

│

├── deployments/

│   ├── gateway-service.yaml

│   ├── order-service.yaml

│   ├── product-service.yaml

│   └── user-service.yaml

│

├── services/

│   ├── gateway-service.yaml

│   ├── order-service.yaml

│   ├── product-service.yaml

│   └── user-service.yaml

│

├── ingress/

│   └── ingress.yaml

│

├── screenshots/

│

├── gateway-service/

├── order-service/

├── product-service/

├── user-service/

│

└── README.md

```



\---



\# Prerequisites



\- Docker Desktop

\- Minikube

\- kubectl

\- Git



\---



\# Start Minikube



```bash

minikube start

```



Verify cluster status:



```bash

minikube status

```



\---



\# Load Docker Images into Minikube



```bash

minikube image load microservices-user-service:latest

minikube image load microservices-product-service:latest

minikube image load microservices-order-service:latest

minikube image load microservices-gateway-service:latest

```



\---



\# Deploy the Application



Deploy all Kubernetes Deployments:



```bash

kubectl apply -f deployments/

```



Deploy all Services:



```bash

kubectl apply -f services/

```



\---



\# Verify Deployment



Check Deployments



```bash

kubectl get deployments

```



Check Pods



```bash

kubectl get pods

```



Check Services



```bash

kubectl get svc

```



\---



\# Port Forward Gateway



```bash

kubectl port-forward service/gateway-service 3003:3003

```



\---



\# API Testing



\## Health Check



```bash

curl http://localhost:3003/health

```



\## Users



```bash

curl http://localhost:3003/api/users

```



\## Products



```bash

curl http://localhost:3003/api/products

```



\## Orders



```bash

curl http://localhost:3003/api/orders

```



Create an Order



```bash

curl -X POST http://localhost:3003/api/orders \\

\-H "Content-Type: application/json" \\

\-d "{\\"userId\\":1,\\"productId\\":2}"

```



\---



\# Screenshots



Include the following screenshots:



\- Running Deployments

\- Running Pods

\- Running Services

\- Gateway Logs

\- Port Forward

\- API Testing



\---



\# Troubleshooting



\## ImagePullBackOff



Ensure Docker images are loaded into Minikube.



```bash

minikube image ls

```



\---



\## Pods Not Starting



```bash

kubectl describe pod <pod-name>

```



\---



\## View Logs



```bash

kubectl logs deployment/gateway-service

```



\---



\# Technologies Used



\- Kubernetes

\- Minikube

\- Docker

\- Node.js

\- Express.js

\- kubectl



\---



\# Author



Rahul Bansal

