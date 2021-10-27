The automation is used to deploy spring petclinic angular application into AWS cloud.

To spin up the required infrastructure in AWS cloud refer https://github.com/kmanvitha30/terraform-petclinic
To deploy the backend spring petclinic rest application refer https://github.com/kmanvitha30/petclinic-rest

## Pre-Requisities:
The machine from which the automation script is executed should have git installed. Requires angular-cli/docker/helm based on the installation method.
```
#git
sudo yum install git -y
git --version

#angular-cli
curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -
sudo yum install nodejs -y
sudo npm install -g @angular/cli@latest 

#docker
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
docker -v

#helm
wget -O helm.tar.gz https://get.helm.sh/helm-v3.5.4-linux-amd64.tar.gz
tar -zxvf helm.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm
helm version
```

## To Run Locally:
1. Clone the git repository and make petclinic-angular as the current working directory.
```
git clone https://github.com/kmanvitha30/petclinic-angular.git
cd petclinic-angular/
```

2. Build and serve:
```
cd docker/
ng serve --open --host 0.0.0.0 --port 4200 --disable-host-check
```

3. Run with Docker:
```
cd docker/
docker build -t <docker_repository>/petclinic-angular:<image_tag> .
docker run -p 8080:8080 <docker_repository>/petclinic-angular:<image_tag>
```

4. With helm:
```
helm install <release_name> helm-petclinic_angular
NOTE : Update the values.yaml prior running.
```

5. The application can be accessed at:
```
http://<endpoint-address>:8080
```