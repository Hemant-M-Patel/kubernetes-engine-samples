# Kubernetes Engine Samples

This repository contains sample applications used in
[Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) tutorials.

See the following resources to learn more:

- [Google Kubernetes Engine - Quickstart](https://cloud.google.com/kubernetes-engine/docs/quickstart)
- [Google Kubernetes Engine - Tutorials](https://cloud.google.com/kubernetes-engine/docs/tutorials)

# Quick Start GCP Kubernetes on Windows with Hello World App

- [Install Git for Windows](https://github.com/git-for-windows/git/releases/download/v2.28.0.windows.1/Git-2.28.0-64-bit.exe)
- [Install Notepad++](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v7.8.8/npp.7.8.8.Installer.x64.exe)
- Do Windows update before Installing Docker
- [Install Docker for Windows](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe)
- Sign up for Free Google Cloud Account using your gmail ID - https://cloud.google.com/
- [Download gCloud tool for Windows](https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe)
- Initialize your Local gcloud env and set the default project
```
gcloud init
```
- Handy way to get current project and set an environment variable
```
gcloud config get-value project
set PROJECT_ID=<project value>
```
- Clone the Repo
```
git clone https://github.com/GoogleCloudPlatform/kubernetes-engine-samples
cd kubernetes-engine-samples/hello-app
```
- Build docker Image
```
docker build -t gcr.io/%PROJECT_ID%/hello-app:v1 .
```
- Run it locally
```
docker run --rm -p 8080:8080 gcr.io/%PROJECT_ID%/hello-app:v1
```
- Push the Image so that we can deploy into k8s cluster
```
gcloud auth configure-docker
docker push gcr.io/%PROJECT_ID%/hello-app:v1
```
Setup GKE
```
gcloud config set project $PROJECT_ID
gcloud config set compute/zone compute-zone
gcloud container clusters create hello-cluster
gcloud compute instances list
kubectl create deployment hello-app --image=gcr.io/%PROJECT_ID%/hello-app:v1
kubectl get pods
kubectl expose deployment hello-app --name=hello-app-service --type=LoadBalancer --port 80 --target-port 8080
kubectl get service
```

## Contributing changes

* See [CONTRIBUTING.md](CONTRIBUTING.md)

## Licensing

* See [LICENSE](LICENSE)
