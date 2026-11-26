to deploy maven on ec2
git clone YOUR_GITHUB_REPOSITORY_URL
cd my-web-app
ls
mvn clean package
ls target/
sudo systemctl enable --now tomcat9
sudo cp target/*.war /var/lib/tomcat9/webapps/
sudo systemctl restart tomcat9
http://YOUR-PUBLIC-IP:8080/YOUR-WAR-NAME

if they ask to make docker image out of macen
git clone YOUR_GITHUB_REPOSITORY_URL
cd YOUR_PROJECT_FOLDER
mvn clean package
ls target/
nano Dockerfile
sudo docker build -t maven-web-app .
sudo docker images
sudo docker run -d --name myapp -p 6060:8080 maven-web-app
http://YOUR-EC2-PUBLIC-IP:6060/YOUR-WAR-NAME

if they ask normally
git clone
cd project
ls
nano dockerfile
sudo docker build -t myapp .
sudo docker images
sudo docker run -d --name mycontainer -p 8080:80 myapp

to push to dockerhub
login
tag image- docker tag IMAGE_NAME YOUR_USERNAME/IMAGE_NAME:latest
push-docker push YOUR_USERNAME/IMAGE_NAME:latest


kubernetes commands
minikube start --driver=docker
minikube status
kubectl get nodes
kubectl create deployment mynginx --image=nginx
kubectl get deployments
kubectl get pods
kubectl describe pods
kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80
kubectl get services
kubectl scale deployment mynginx --replicas=4
kubectl get pods
kubectl get deployments
kubectl port-forward svc/mynginx 8081:80
