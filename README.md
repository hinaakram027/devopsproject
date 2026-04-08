## Step 1: Create EC2 Instance
 IAM user with **access keys and secret access keys**
 ## Step 2: Install ```AWS CLI```, ```Kubectl```, ```EKSCTL```:
 ```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

apt install unzip

unzip awscliv2.zip
```
- ```Kubectl``` - kubectl is the command-line tool used to interact with Kubernetes clusters.
```
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.30.2/2024-07-12/bin/linux/amd64/kubectl

chmod +x kubectl

mv kubectl /usr/local/bin/kubectl
```    
- ```EKSCTL``` - eksctl is a command-line tool for managing Amazon EKS (Elastic Kubernetes Service) clusters.
```
curl -LO "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz"

tar -xzf eksctl_Linux_amd64.tar.gz

sudo mv eksctl /usr/local/bin/

eksctl version
```
## Step 3: AWS Configure - 
        ○ Access Key - Your_Access_Key
        ○ Access Secret Key - Your Access_secret_key
<img width="1365" height="727" alt="iam role configure pic from vscode pic" src="https://github.com/user-attachments/assets/6c60de54-458a-40af-9eb0-a0becf1cb694" />
   
## Step 4: Install Terraform 
```
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```
## terraform init
<img width="1365" height="720" alt="terraform module downloading stage pic 1" src="https://github.com/user-attachments/assets/de35a159-c914-44ce-b5eb-2528d66b8244" />
<img width="1365" height="719" alt="terraform successfully initilization pic 2" src="https://github.com/user-attachments/assets/008e2163-bd54-40f0-97a1-d7c0bcde0b42" />

## terraform plan
<img width="1365" height="723" alt="terraform plan pic 1" src="https://github.com/user-attachments/assets/01aca206-6645-4b45-b604-31107c81916e" />
<img width="1365" height="719" alt="terraform plan pic 2" src="https://github.com/user-attachments/assets/9c6def60-898f-45b0-af0e-0c301d679791" />
<img width="1365" height="721" alt="terraform plan pic 3" src="https://github.com/user-attachments/assets/8a5548ef-97b0-43b7-b4fb-c60d23a49362" />
<img width="1365" height="719" alt="terraform plan pic 4" src="https://github.com/user-attachments/assets/a7319b5c-fec0-42d7-a04e-77090aa0eeaa" />
<img width="1365" height="720" alt="terraform plan pic 5" src="https://github.com/user-attachments/assets/34e8f140-be29-4c5e-9922-5ba79841cc4d" />
<img width="1365" height="717" alt="terraform plan pic 6" src="https://github.com/user-attachments/assets/d0a6bac4-7b3d-4290-bf47-5d05d2d0bf21" />

## terraform apply
<img width="1365" height="719" alt="eks cluster apply creation pic 1" src="https://github.com/user-attachments/assets/9f05469a-45d4-4602-9286-a910829bdedd" />
<img width="1365" height="718" alt="eks cluster apply creation pic 2" src="https://github.com/user-attachments/assets/42417be3-3c3c-4747-971b-f112b207f411" />
<img width="1365" height="719" alt="eks cluster apply creation pic 3" src="https://github.com/user-attachments/assets/ebb47bac-464d-4131-8414-0e53a50efe81" />
<img width="1365" height="720" alt="eks cluster apply creation pic 4" src="https://github.com/user-attachments/assets/8079559e-7098-4632-82b1-fb649c7f1122" />
<img width="1365" height="718" alt="eks cluster apply creation pic 5" src="https://github.com/user-attachments/assets/52484939-671f-46e9-a6c5-fbd9ccc3acb8" />
<img width="1365" height="720" alt="eks cluster apply creation pic 6" src="https://github.com/user-attachments/assets/e6fdfb27-6329-48f5-8a38-6dd618307ff2" />

## Step 5: AWS Configure EKS Cluster

```
eksctl  create cluster --name my-devops-project --region us-east-2
```

```
aws eks update-kubeconfig --name my-devops-project --region us-east-2
```
<img width="1365" height="722" alt="eks cluster aws configuration pic" src="https://github.com/user-attachments/assets/8fc9e756-4b1f-4171-8a90-5b7dc618e784" />
<img width="1365" height="676" alt="eks complete creation pic aws dashboard" src="https://github.com/user-attachments/assets/0bdde337-a3a3-4d9e-9183-c3099ab96f43" />
<img width="1365" height="678" alt="eks cluster vpc pic" src="https://github.com/user-attachments/assets/9615cba4-aad4-495b-91b2-af69be05ee95" />

## Step 6: Docker Installation 

```
sudo apt install docker.io -y
```

## Step 7: Give Permission Docker 

```
sudo usermod -aG docker $USER
sudo chmod 777 /var/run/docker.sock
```
<img width="1361" height="478" alt="docker hub images pic" src="https://github.com/user-attachments/assets/fcca19f2-2780-4142-b3b8-bbdc01b84589" />

## Step 8: SonarQube Installation 

```
docker run -itd --name sonarqube-server -p 9000:9000 sonarqube:lts-community
```
<img width="1365" height="680" alt="sonarqube installation access page pic" src="https://github.com/user-attachments/assets/60235623-653e-4e21-9e08-82bdaf98e414" />
<img width="1365" height="676" alt="sonarqube correct jenkins integration pic" src="https://github.com/user-attachments/assets/59ab6da3-62c0-4b45-a3b0-b81ade3d77c2" />
<img width="1365" height="635" alt="sonarqube test passed report" src="https://github.com/user-attachments/assets/72e946cd-558f-4684-920c-06febc5a6c49" />

## Step 9: Trivy Installation 

```
sudo apt-get install wget gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```

## Step 10: Jenkins Installation

```
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```

```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```
<img width="1364" height="717" alt="jenkins password decode vscode pic" src="https://github.com/user-attachments/assets/050de3ab-fce8-4c94-9fbf-3ef0c1a05060" />
<img width="1365" height="679" alt="jenkins sonar credential add pic" src="https://github.com/user-attachments/assets/1a8d0b6a-ed1e-458f-a27e-a194ca95716c" />
<img width="1365" height="675" alt="docker credential add in jenkins" src="https://github.com/user-attachments/assets/a0992bf2-1556-4a3c-a341-eeb29002df66" />
<img width="1364" height="634" alt="jenkins pipeline pic 1 writing" src="https://github.com/user-attachments/assets/366b917e-0db5-4919-a671-72cf9f89ccf1" />
<img width="1365" height="634" alt="jenkins pipeline writing pic 2" src="https://github.com/user-attachments/assets/36aee1ba-b29c-48d2-99de-648d7660c068" />
<img width="1364" height="632" alt="jenkins pipeline writing pic 3" src="https://github.com/user-attachments/assets/292a5ca6-76a8-44c1-ae0e-042ee6dfe0ea" />
<img width="1365" height="629" alt="jenkins pipeline writing pic 4" src="https://github.com/user-attachments/assets/c7ecadf6-05f6-46ff-b355-8817fa5fbb67" />
<img width="1365" height="631" alt="jenkins pipeline successful correct name pipeline pic" src="https://github.com/user-attachments/assets/8dd29272-68ec-42f0-91c2-538e37d9f878" />

## Step 10: Install Argocd

```
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```
- Retrieve the initial admin password for ArgoCD:
```
kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
<img width="1365" height="678" alt="argocd main page" src="https://github.com/user-attachments/assets/73036e42-f5bd-4212-a9c8-aa5a759e54f9" />

## Step 11: Install Helm
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```
```
chmod 700 get_helm.sh
```
```
./get_helm.sh
 DESIRED_VERSION=v3.8.2 bash get_helm.sh
 curl -L https://git.io/get_helm.sh | bash -s -- --version v3.8.2
```
```
helm version
```
## Step 11: Add Helm Chart to local Client
```
helm repo add stable https://charts.helm.sh/stable
```
## Step 12: Add Prometheus Helm Repository
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
```
kubectl create namespace prometheus
```
## Step 13: Install Prometheus using Helm 
```
helm install stable prometheus-community/kube-prometheus-stack -n prometheus
```
## Step 14: Expose Prometheus and Grafana to the External World through LoadBalancer Edit the Helm File
```
kubectl edit svc stable-kube-prometheus-sta-prometheus -n prometheus
```
## Step 15: Access LoadBalancer
```
kubectl get svc -n prometheus
```

<img width="1364" height="674" alt="access prometheus through load balancer" src="https://github.com/user-attachments/assets/04806562-293e-40eb-bdb4-484c7b83dd26" />

## Step 16: Edit Grafana helm Chart for LoadBalancer
```
kubectl edit svc stable-grafana -n prometheus
```
## Step 17: Access LoadBalancer
```
kubectl get svc -n prometheus
```
## Step 18: Grafana Password Decode
```
kubectl get secret --namespace prometheus stable-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
<img width="1365" height="623" alt="grafana password access" src="https://github.com/user-attachments/assets/67cabe94-d01f-4894-8bbd-5aeee63cf409" />

<img width="1365" height="637" alt="grafana welcome dshboard" src="https://github.com/user-attachments/assets/8ab7ac40-e60e-47b1-bc7f-4cda71fd5872" />






















































        




