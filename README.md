# Deploying a Gen AI Application with Vector Store in Firestore

After amazing blog post from [Suds Kumar](https://sudsk.medium.com/) ["Building a RAG application with vector search in Firestore"](https://medium.com/google-cloud/building-a-rag-application-with-vector-search-in-firestore-71da2e6e7e77) we’ll take the next step: deploying this Gen AI-powered application using Cloud Run.

This repository contains all needed for creating an Artifact Registry, containerizing the application with Docker, and deploying it to Cloud Run for scalable, serverless deployment.

## Prerequisites
Ensure you have:
- Firestore and your vector store configured (as per the Kumar's [post](https://medium.com/google-cloud/building-a-rag-application-with-vector-search-in-firestore-71da2e6e7e77)).
- Google Cloud SDK installed and authenticated to your project.
- Enabled the following APIs:
  - Artifact Registry
  - Cloud Run
  - Vertex AI
  - Cloud IAM
- Billing enabled on the project.
