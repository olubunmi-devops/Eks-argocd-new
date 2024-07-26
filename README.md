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
# Login to Argocd
When the password has been retrieved,login into Argocd with 
![image](https://github.com/user-attachments/assets/9d987499-b9a9-4d94-a8bf-cf8dff9b08d0)





