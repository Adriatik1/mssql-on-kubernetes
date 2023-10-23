# MSSQL Database on Kubernetes

This project deploys a Microsoft SQL Server (MSSQL) database on a Kubernetes cluster using YAML configuration files.

## Prerequisites

Before you begin, make sure you have the following:

- A running Kubernetes cluster.
- `kubectl` command-line tool configured to work with your cluster.
- Docker or another container runtime to build and push container images if needed.

## Configuration Files

The project includes three primary YAML configuration files:

1. **sql-secret.yaml**: Defines a Kubernetes Secret containing the SA password for MSSQL. Ensure that the password is properly encoded in Base64.
   
2. **sql-pvc.yaml**: Configures a Persistent Volume Claim (PVC) to request storage for the MSSQL data. Adjust the `storage` and `accessModes` according to your needs.

3. **sql-db.yaml**: Deploys a Service and Deployment for MSSQL. Note that you should give distinct names for the Service and Deployment.

## Deployment

1. Apply the configuration files in the following order:

   ```bash
   kubectl apply -f sql-secret.yaml
   kubectl apply -f sql-pvc.yaml
   kubectl apply -f sql-db.yaml
