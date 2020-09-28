How to Create and Deploy your flask app on GKE 

1. Fork and clone this repository in a google cloud shell 
2. Build a docker image: docker build -t [name of image] . 
3. Tag docker image: docker tag [name of image] gcr.io/[project-id]/[name of image]:version1.0 
4. Push docker image to container registry: docker push gcr.io/[project-id]/[name of image]:version1.0 
5. Pull docker image from conatiner registry: docker pull gcr.io/[project-id]/[name of image]:version1.0 
6. Create new GKE cluster: gcloud container clusters create [cluster name] --num-nodes 1 --enable-basic-auth --issue-client-certificate --zone [zone name] 
7. Replace image with you image name in deployment.yaml 
8. Deploy resource on cluster: kubectl apply -f deployment.yaml 
9. Create service: kubectl apply -f service.yaml 
10. Get external ip for service: kubectl get svc 
11. Enter ip in browser on port 80 to see your flask app 
