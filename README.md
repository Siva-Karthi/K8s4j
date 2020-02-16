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
echo "$(sudo minikube ip) kube.local" | sudo tee -a /etc/hosts
and then
http://kube.local
http://kube.local/echo/test

