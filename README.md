# K8s4j
Java app in kubernetes

#run app in the host  
mvn spring-boot:run

#build optimized docker image
mvn compile jib:build

#install minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
&& sudo install minikube-linux-amd64 /usr/local/bin/minikube

#start kubernetes cluster in local
sudo minikube start --vm-driver=none

#create kubernetes resources
sudo kubectl create -f deployment/kubernetes/

#Access the service
sudo minikube addons enable ingress
echo "$(sudo minikube ip) kube.local" | sudo tee -a /etc/hosts
and then
http://kube.local
http://kube.local/echo/test

#deploy and run using helm 
//helm create k8s4j - to create a chart
helm install example ./k8s4j --set service.type=NodePort - deployment
// 1. Get the application URL by running these commands:
//  export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services alpha-release-k8s4j)
//  export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
//  echo http://$NODE_IP:$NODE_PORT

other useful helm commands
helm list
helm uninstall example