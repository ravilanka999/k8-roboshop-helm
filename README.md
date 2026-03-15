# Roboshop Helm Charts

Helm charts for deploying the Roboshop microservices application on Amazon EKS.

## Charts Included

| Chart | Type | Description |
|---|---|---|
| catalogue | Deployment | Product catalogue service |
| cart | Deployment | Shopping cart service |
| user | Deployment | User authentication service |
| payment | Deployment | Payment processing service |
| shipping | Deployment | Shipping calculation service |
| frontend | Deployment | Nginx frontend |
| mongodb | StatefulSet | MongoDB database |
| mysql | StatefulSet | MySQL database |
| redis | StatefulSet | Redis cache |
| rabbitmq | StatefulSet | RabbitMQ message broker |

## Chart Structure
```
<service>/
├── Chart.yaml           # Chart metadata
├── values.yaml          # Default values
└── templates/
    ├── deployment.yaml  # Kubernetes Deployment
    ├── service.yaml     # Kubernetes Service
    ├── configmap.yaml   # Environment configuration
    └── hpa.yaml         # Horizontal Pod Autoscaler
```

## Features

- ✅ HPA configured for all stateless services
- ✅ StatefulSets for databases with persistent storage
- ✅ ConfigMaps for environment-specific configuration
- ✅ Namespace isolation
- ✅ EBS StorageClass for persistent volumes

## Usage
```bash
# Deploy a single chart
helm install catalogue ./catalogue -n roboshop

# Deploy all charts
for chart in catalogue cart user payment shipping frontend mongodb mysql redis rabbitmq; do
  helm install $chart ./$chart -n roboshop
done
```

## Related Repos

- [eks-argocd](https://github.com/ravilanka999/eks-argocd) — GitOps platform
- [catalogue-cd](https://github.com/ravilanka999/catalogue-cd) — CD pipeline example
