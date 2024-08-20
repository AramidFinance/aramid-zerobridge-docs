# Setup Aramid Soldier and Indexer via Kubernetes Node with Linode

## This setup consists of the following key components:

- Aramid Soldier: Runs as a StatefulSet with persistent storage
- Aramid Indexer: Runs as a Deployment
- Ingress: Provides external access to the Indexer
- ConfigMap: Stores Indexer configuration
- Prerequisites
- Linode account
- kubectl installed (version compatible with your cluster)
- jq installed
- Access to Aramid's GitHub repository
- Basic understanding of Kubernetes concepts

## 1. Linode-Specific Setup

1.1. Create Kubernetes Cluster
- Log into Linode account
- Navigate to Kubernetes section
- Click "Create Cluster"
- Configure cluster:
    - Name: Choose a meaningful name (e.g., aramid-cluster)
    - Region: Select based on your geographical needs
    - Kubernetes Version: Choose the latest stable version
    - Node Pool: Configure based on Aramid's requirements
- Create cluster (this process may take 5-10 minutes)

1.2. Access Cluster Configuration
- Select your cluster in Linode dashboard
- Go to "Configuration" tab
- Download Kubeconfig file

1.3. Firewall Configuration
- Ensure inbound rules allow:
    - TCP 80, 443 (HTTP/HTTPS for Ingress)
    - TCP 6443 (Kubernetes API server)
- Consider restricting access to trusted IP ranges for enhanced security

1.4. (Optional) Setup Load Balancer
- Create Node Balancer if needed for high availability
- Configure to distribute traffic among nodes
- Ensure health checks are properly configured

## 2. Configure Kubernetes Cluster Access

2.1. Set the KUBECONFIG environment variable:
```bash 
export KUBECONFIG=/path/to/aramidsoldier-kubeconfig.yaml
```
Replace /path/to/ with the actual path to your downloaded Kubeconfig file.

2.2. Verify the configuration:
```bash
kubectl version --short
```

This should display both client and server versions.

2.3. (Optional) For persistent configuration:
```bash
echo "export KUBECONFIG=/path/to/aramidsoldier-kubeconfig.yaml" >> ~/.bashrc
```

Use ~/.zshrc for Zsh.

2.4. Apply the configuration:
```bash
source ~/.bashrc # or ~/.zshrc for Zsh
```

WARNING: The kubeconfig file contains sensitive information. Ensure it's stored securely and never shared publicly.

## 3. Setup Kubernetes Dashboard

3.1. Install the Kubernetes Dashboard:
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

3.2. Create a dashboard user:
```bash
kubectl apply -f https://raw.githubusercontent.com/scholtz/AlgorandNodes/main/kubernetes/kmd-fi/service-user.yaml
```

3.3. Get the dashboard token:
```bash
kubectl get secret admin-token -n kubernetes-dashboard -o jsonpath="{.data.token}" | base64 --decode
```

Save this token securely for dashboard access.

3.4. Start the kubectl proxy:
```bash
kubectl proxy
```

3.5. Access the dashboard at:

http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

3.6. Use the token from step 3.3 to log in.

## 4. Install Aramid Soldier Application

4.1. Apply the Aramid Soldier configuration:
```bash
kubectl apply -f https://raw.githubusercontent.com/scholtz/AlgorandNodes/main/kubernetes/aramid-linode-example/statefulset.yaml
```

4.2. Verify the deployment:
```bash
kubectl get pods
kubectl get services
```

Ensure all pods are in 'Running' state and services are properly created.

## 5. Install Aramid Indexer

5.1. Apply the Aramid Indexer deployment:
```bash
kubectl apply -f deployment.yaml
```

5.2. Verify the Indexer deployment:
```bash
kubectl get pods -n aramid-indexer-mainnet
```

5.3. Apply the Ingress configuration:
```bash
kubectl apply -f ingress.yaml
```

5.4. Verify the Ingress:
```bash
kubectl get ingress -n aramid-indexer-mainnet
```
Ensure the Ingress is properly configured and has an external IP assigned.

## 6. Configure Aramid Indexer

6.1. Create a ConfigMap for the Indexer configuration:
```bash
kubectl create configmap aramidmain-indexer-conf --from-file=conf -n aramid-indexer-mainnet
```

6.2. Update Indexer configuration:
```bash
./update-config.sh
```

This script performs the following actions:

- Deletes the existing ConfigMap
- Creates a new ConfigMap from the conf directory
- Applies the deployment configuration
- Restarts the Indexer deployment
- Verify the ConfigMap creation and deployment restart to ensure changes are applied.

## 7. Monitoring and Maintenance
Check pod status:
```bash
kubectl get pods -n aramid-indexer-mainnet
```
View pod logs:
```bash
kubectl logs <pod-name> -n aramid-indexer-mainnet
```

Describe pod details:
```bash
kubectl describe pod <pod-name> -n aramid-indexer-mainnet
```

## 8. Aramid Indexer Commands

8.1. Check the status of the Indexer:
```bash
kubectl get deployment aramid-indexer-mainnet -n aramid-indexer-mainnet
```

8.2. View Indexer logs:
```bash
kubectl logs deployment/aramid-indexer-mainnet -n aramid-indexer-mainnet
```

8.3. Restart the Indexer:
```bash
kubectl rollout restart deployment/aramid-indexer-mainnet -n aramid-indexer-mainnet
```

8.4. Update Indexer configuration:
```bash
./update-config.sh
```

8.5. Scale the number of Indexer replicas:
```bash
kubectl scale deployment aramid-indexer-mainnet --replicas=<desired-number> -n aramid-indexer-mainnet
```

Replace <desired-number> with the appropriate value for your deployment.

## Troubleshooting

For pod issues:
```bash
kubectl get events --sort-by=.metadata.creationTimestamp -n aramid-indexer-mainnet
```

For networking issues, check Linode firewall settings and Ingress configuration

For Indexer configuration issues, verify the contents of the ConfigMap:
```bash
kubectl describe configmap aramidmain-indexer-conf -n aramid-indexer-mainnet
```

If pods are stuck in 'Pending' state, check node resources:
```bash
kubectl describe nodes
```

For persistent volume issues:
```bash
kubectl get pv,pvc -n aramid-indexer-mainnet
```

Remember to consult Aramid's official documentation for specific configurations or updates. This guide provides a general overview and may need adjustments based on your specific setup or Aramid's latest requirements.