## SIT737 Task 10.1P 

---

### Steps Followed:

1. **Installed Google Cloud CLI** on the local machine to interact with GCP services.
2. **Initialized and authenticated** using `gcloud init`.
3. **Created a Docker Artifact Registry** using the command:
   ```bash
   gcloud artifacts repositories create node-app-repo --repository-format=docker --location=us-central1
   ```
4. **Configured Docker to authenticate** with Artifact Registry:
   ```bash
   gcloud auth configure-docker us-central1-docker.pkg.dev
   ```
5. **Built a Docker image** for the Node.js app and tagged it for the registry:
   ```bash
   docker build -t us-central1-docker.pkg.dev/PROJECT_ID/node-app-repo/node-k8s-app .
   ```
6. **Pushed the Docker image** to Artifact Registry:
   ```bash
   docker push us-central1-docker.pkg.dev/PROJECT_ID/node-app-repo/node-k8s-app
   ```
7. **Created a custom VPC network** in GCP for use with the Kubernetes cluster.
8. **Created a GKE cluster** using the `gcloud` CLI with the custom network.
9. **Retrieved cluster credentials** for `kubectl`:
   ```bash
   gcloud container clusters get-credentials node-k8s-cluster --region=us-central1
   ```
10. **Deployed the app** to Kubernetes using `deployment.yaml` and exposed it via `service.yaml`.
11. **Verified pod status** and **external service IP** using:
    ```bash
    kubectl get pods
    kubectl get service node-app-service
    ```
12. **Accessed the deployed app** through the external LoadBalancer IP in a web browser.
13. **Monitored cluster and pod resource usage** using:
    ```bash
    kubectl top nodes
    kubectl top pods
    ```
14. **Accessed system-level logs** via Google Cloud Logs Explorer (container logs not available due to permission limitations).
15. **Verified cluster health and resource info** through the GCP Console.

---

The deployment was successful, and the application was made publicly accessible with performance and monitoring tools validated.
