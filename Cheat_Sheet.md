Export variable:
```bash
export PROJECT_ID=ylebi-rnd
```

Create an Artifact Registry:
```bash
gcloud artifacts repositories create test-repo \
    --repository-format=docker \
    --location=us-central1 \
    --description="Docker repository for food-safety image"
```

Make sure your Docker client is authenticated with:
```bash
gcloud auth configure-docker us-central1-docker.pkg.dev
```

Build Docker image:
```bash
docker build -t us-central1-docker.pkg.dev/$PROJECT_ID/test-repo/food-safety:latest -f Dockerfile .
```

Push Docker image to Artifact Registry:
```bash
docker push us-central1-docker.pkg.dev/$PROJECT_ID/test-repo/food-safety:latest
```

Deploy the container to Cloud Run with the following command:
```bash
gcloud run deploy food-safety-service \
    --image=us-central1-docker.pkg.dev/$PROJECT_ID/test-repo/food-safety:latest \
    --region=us-central1 \
    --allow-unauthenticated \
    --min-instances=0 \
    --max-instances=1
```

To allow all users to invoke the service, run:
```bash
gcloud beta run services add-iam-policy-binding \
    --region=us-central1 \
    --member=allUsers \
    --role=roles/run.invoker \
    food-safety-service
```
