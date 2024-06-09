![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/6bdfa9ab-7f53-4789-b624-072dcd8745d8)

Command to **install AWSCLI & install Unzip**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1ee0355d-de28-4d7c-bff4-ccde222b7d9a)

Command to unzip

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/a4058fab-7aca-4a98-8418-dc3df6f5e6ac)

Command to install AWS


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/c8994951-f36e-4ea7-a7f0-638c4797fcf7)

Command to Configure AWS

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1569bea4-3f45-4714-a657-db5e50f6703a)

For access Id 

Go to **IAM user**

click on **SECurity Credentials**


click on **create access key**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/01ffa759-2db7-470f-b129-974a6a800a67)

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/9c6b77e5-bf5b-40fc-b5b1-d9193a9ab0a2)

we created the key successfully

Download the csv fil for the credentials

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/c0bfa3ee-c3cb-4aed-82fc-6b36672a62f8)

steps to configure AWS

Write the region name according to your region
and keep default output format as blank

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/d903af9a-559f-4fb0-8778-39ca310f68ca)

To check it is configure or not 

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/7c54d45f-74ef-47c3-a84a-fe69aae89ac2)


Command to install kubectl

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1a8c6dc7-3337-4c82-9212-407ec2d3fb13)


Command to install eksctl

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/8ba11cd7-7cf2-4bbb-b366-6946becbb40d)


Creation of EKS Cluster

eksctl create cluster --name=my-eks924 \
                      --region=ap-south-1 \
                      --zones=ap-south-1a,ap-south-1b \
                      --version=1.30 \
                      --without-nodegroup



![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/8d29171d-c89e-40eb-a181-19facdd34a3a)

