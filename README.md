# Use of [nginx.ingress.kubernetes.io/rewrite-target](http://nginx.ingress.kubernetes.io/rewrite-target) annotation

This repository contains the code that will set up the Python application with a Dockerfile and an Ingress object using the nginx.ingress.kubernetes.io/rewrite-target annotation.

## Application Deployment
run following commands to deploy the application into your kubernetes cluster

```sh
$ kubectl apply -f Deployment.yaml
$ kubectl apply -f service.yaml
$ kubectl apply -f ingress.yaml
```
## On Minikube
if you want to test your application on minikube then you need to enable the ingress addon on your minikube 
```sh
$ minikube addons enable ingress
```
followed by below commands
```sh
$ curl $(minikube ip)/home
or 
$ curl $(minikube ip)/home/user
```
## On Other kubernetes environment
for running your other kubernetes environment such as AKS and EKS you need to deploy ingress controller manually into your kubernetes cluster and then run 
```sh
$ kubeclt get service 
```
 and copy the load balancer or Nodeport External IP for example
 ```sh
$ curl nginx-controller-expernal-ip/home 
```
 
**Note!**
If you want to build your own docker image then you can run this command
```sh
$ docker build -t your-tag-name --file addDockerfile .
```
but then you need to replace the image name from the deployment file with your image name.
