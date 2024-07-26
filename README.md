# BootStrap EKS Cluster with ArgoCD using Terraform,Helm.

Step 1. Clone the repository.Move  into the Eks folder which contains the Terraform files to provision your cluster on AWS and perform the required terraform operations below.

terraform init
terraform plan
terraform apply

![image](https://github.com/user-attachments/assets/19bee2b6-b3c2-476e-b07b-fec5bb59a6aa)
![image](https://github.com/user-attachments/assets/b0e91f6b-9f0e-4e14-ae81-135381a70139)
The terraform configuration provisions the following listed below:
EKS cluster on AWS
Node and Node group using SPOT instances
Update Kube config on the machine you’re running terraform from.
![image](https://github.com/user-attachments/assets/f1c02ebb-b559-4395-ba92-8ff82dcf9749)

Install ArgoCD helm chart on the provisioned cluster
![image](https://github.com/user-attachments/assets/1482bc3a-0bf6-473b-9f7e-ec751bfb845c)

![image](https://github.com/user-attachments/assets/9bc8e698-73b9-4d03-968d-1c521489ce93)

![image](https://github.com/user-attachments/assets/41319659-4667-4e80-bef8-5b041e8007ce)
![image](https://github.com/user-attachments/assets/e20b69c3-1314-47ff-b561-9f41074f4d52)

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo![image](https://github.com/user-attachments/assets/dab31053-2fc2-47d5-83d1-7f037198d10b)
## 3.Login to Argocd
When the password has been retrieved,login into Argocd with 
![image](https://github.com/user-attachments/assets/9d987499-b9a9-4d94-a8bf-cf8dff9b08d0)
## 4.Connect GitHub Repository to ArgoCD:

Once logged in successfully, connect the GitHub repo that contains the manifest with the following command:
argocd repo add https://github.com/username/repourl --username <your-github-username> --password <your-personal-access-token>
![image](https://github.com/user-attachments/assets/1550021e-e7ba-4b0c-9daa-c7d2f1dd6806)


Note: To get your GitHub password, use your GitHub token, which can be generated in developer’s settings.

## 5.Add Your Cluster to ArgoCD:

Once your repo has been connected successfully, add your cluster to the ArgoCD server using the following command:

kubectl config get-contexts
argocd cluster add <context-name>

![image](https://github.com/user-attachments/assets/3f8bc397-2ddb-4820-a460-891a208727e7)
## 6.Create and Sync Your Application:

Once the cluster has been added successfully, proceed to create your app and configure your ArgoCD using:

argocd app create appname \
   --repo https://github.com/username/repourl \
   --path terraform/ \
   --dest-server https://kubernetes.default.svc \
   --dest-namespace argocd
   ![image](https://github.com/user-attachments/assets/751629f3-8287-4dd7-b9dc-eae8f5e2ce4c)
  ## 7. Sync Your Application:

Finally, sync your app using the following command:

argocd app sync danoapp
![image](https://github.com/user-attachments/assets/3f48dca5-21ea-4033-9a56-57d34fe793ba)
Once the sync is successful, you can log in to your ArgoCD via the browser to check it out.

![image](https://github.com/user-attachments/assets/24b718cd-2c73-40f1-8e5f-36460e333ad9)



