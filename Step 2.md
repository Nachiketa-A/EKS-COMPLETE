After connecting to your EC2 instance using MobaXterm, you can execute the following commands to update the package lists, install AWS CLI, and configure it. Here's a detailed step-by-step guide:

# 1. Installation of AWS CLI

1. **Connect to Your EC2 Instance Using MobaXterm**
   - Open MobaXterm.
   - Start a new SSH session with the IP address and username (`ubuntu`).
   - Use the `.pem` key file for authentication.

2. **Update Package Lists**
   - Run the following command to update the package lists:
     ```bash
     sudo apt update
     ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/6bdfa9ab-7f53-4789-b624-072dcd8745d8)

3. **Install AWS CLI**

   - Install the `unzip` package to handle zip files:
     ```bash
     sudo apt install unzip
     ```

   - Download the AWS CLI version 2 bundle:
     ```bash
     curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
     ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/6bdfa9ab-7f53-4789-b624-072dcd8745d8)

   - Unzip the downloaded bundle:
     ```bash
     unzip awscliv2.zip
     ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1ee0355d-de28-4d7c-bff4-ccde222b7d9a)

   - Install AWS CLI:
     ```bash
     sudo ./aws/install
     ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/a4058fab-7aca-4a98-8418-dc3df6f5e6ac)

4. **Configure AWS CLI**
   - Run the following command to configure AWS CLI:
     ```bash
     aws configure
     ```

   - You will be prompted to enter your AWS access key ID, secret access key, region name, and output format. These credentials are provided by your IAM user.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1569bea4-3f45-4714-a657-db5e50f6703a)

### Commands Summary

```bash
sudo apt update
sudo apt install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

By following these steps, you will have successfully installed and configured AWS CLI on your EC2 instance

# 2. Create access keys for your IAM user and configure the AWS

### Step-by-Step Guide

1. **Go to IAM User in AWS Management Console**

   - Open the [AWS Management Console](https://aws.amazon.com/console/) and log in with your IAM user credentials.

2. **Navigate to IAM**

   - In the AWS Management Console, search for and select **IAM** (Identity and Access Management).

3. **Select Your IAM User**

   - In the IAM dashboard, click on **Users** in the left-hand menu.
   - Click on the IAM user for whom you want to create access keys (e.g., `eks-admin`).
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/01ffa759-2db7-470f-b129-974a6a800a67)

4. **Go to Security Credentials**

   - In the user's details page, click on the **Security credentials** tab.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/9c6b77e5-bf5b-40fc-b5b1-d9193a9ab0a2)

5. **Create Access Key**

   - Scroll down to the **Access keys** section.
   - Click on the **Create access key** button.

6. **Download or Copy the Access Key**

   - A dialog will appear showing your new Access Key ID and Secret Access Key.
   - **Important**: Copy the Access Key ID and Secret Access Key. You won't be able to see the Secret Access Key again after this dialog is closed.
   - Optionally, download the `.csv` file containing your credentials.

### Configure AWS CLI

Now that you have your Access Key ID and Secret Access Key, you can configure the AWS CLI on your EC2 instance.

1. **Connect to Your EC2 Instance Using MobaXterm**

   - Open MobaXterm.
   - Start a new SSH session with the IP address and username (`ubuntu`).
   - Use the `.pem` key file for authentication.

2. **Run AWS Configure Command**

   - In the terminal, run:
     ```bash
     aws configure
     ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/c0bfa3ee-c3cb-4aed-82fc-6b36672a62f8)

   - You will be prompted to enter the following information:
     - **AWS Access Key ID**: Paste the Access Key ID you copied earlier.
     - **AWS Secret Access Key**: Paste the Secret Access Key you copied earlier.
     - **Default region name**: Enter your desired region (e.g., `us-west-2`).
     - **Default output format**: Enter your desired format (e.g., `json`).


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/d903af9a-559f-4fb0-8778-39ca310f68ca)

To check it is configure or not 

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/7c54d45f-74ef-47c3-a84a-fe69aae89ac2)

---
---

# 3. Install kubectl

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

