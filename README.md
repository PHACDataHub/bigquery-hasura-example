## Using Hasura on Big Query 

*Note - some better instructions in the Hasura docs listed in the referenece section, these are just quick notes*
### Set up 
1. Set up service account
* IAM & Admin > Service Accounts > Create Service Account
* Name and give roles: BigQuery Metadata Viewer, BigQuery Data Viewer, BigQuery Job User
* Create a json key

2. Environment Variables
* Add key to BIGQUERY_SA_ACCOUNT variable and add your GCP project ID to PROJECT_ID in .env

### To use
Start up
```
docker compose up -d
```
Go to http://localhost:8080/console

Data > Connect Database > BigQuery > Connect Existing Database

* Give Database a name, 
* Connect Database via - use env var BIGQUERY_SA_ACCOUNT 
Project ID - use env var PROJECT_ID
* Datasets - select Datasets and list BigQuery Dataset being used eg cansim_tables


When done, stop and remove containers
```
docker compose down -v
```
### Next Steps
* Add React UI
* Deploy (https://hasura.io/docs/latest/deployment/deployment-guides/kubernetes/, https://hasura.io/docs/latest/deployment/deployment-guides/google-kubernetes-engine-cloud-sql/)

### References
* https://hasurahq.medium.com/tutorial-get-instant-graphql-apis-on-bigquery-with-hasurax-eb18f068bb7a
* https://hasura.io/docs/latest/databases/bigquery/getting-started/docker/
* https://hasura.io/docs/latest/deployment/deployment-guides/docker/#run-the-docker-container-with-an-admin-secret-env-var



<!-- wget https://raw.githubusercontent.com/hasura/graphql-engine/stable/install-manifests/kubernetes/deployment.yaml
wget https://raw.githubusercontent.com/hasura/graphql-engine/stable/install-manifests/kubernetes/svc.yaml

https://kubernetes.io/docs/tasks/configure-pod-container/translate-compose-kubernetes/

kompose convert
minikube start
kubectl apply -f data-connector-agent-service.yaml,graphql-engine-service.yaml -->
 
