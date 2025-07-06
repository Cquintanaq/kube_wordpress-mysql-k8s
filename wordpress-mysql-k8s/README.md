# WordPress and MySQL on Kubernetes

This project contains the necessary Kubernetes configuration files to deploy a WordPress application along with a MySQL database. The deployment is structured to ensure that both applications can communicate effectively within a Kubernetes cluster.

## Project Structure

```
wordpress-mysql-k8s
├── k8s
│   ├── wordpress-deployment.yaml      # Deployment configuration for WordPress
│   ├── wordpress-service.yaml         # Service configuration for WordPress
│   ├── mysql-deployment.yaml          # Deployment configuration for MySQL
│   ├── mysql-service.yaml             # Service configuration for MySQL
│   └── namespace.yaml                 # Namespace configuration
├── .gitignore                         # Git ignore file
└── README.md                          # Project documentation
```

## Deployment Instructions

1. **Set up the Kubernetes Namespace**:
   Apply the namespace configuration to create a dedicated namespace for the applications.
   ```
   kubectl apply -f k8s/namespace.yaml
   ```

2. **Deploy MySQL**:
   First, deploy the MySQL database.
   ```
   kubectl apply -f k8s/mysql-deployment.yaml
   kubectl apply -f k8s/mysql-service.yaml
   ```

3. **Deploy WordPress**:
   After MySQL is up and running, deploy the WordPress application.
   ```
   kubectl apply -f k8s/wordpress-deployment.yaml
   kubectl apply -f k8s/wordpress-service.yaml
   ```

4. **Accessing the Applications**:
   Once both applications are deployed, you can access WordPress through the service defined in `wordpress-service.yaml`. Make sure to check the service type (LoadBalancer or NodePort) to determine how to access it.

## Notes

- Ensure that your Kubernetes cluster has sufficient resources to run both applications.
- Modify the YAML files as necessary to fit your specific requirements, such as resource limits, environment variables, and persistent storage configurations.