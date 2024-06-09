# Step 2. Installation and Configuration of AWS CLI, Kubectl, Eksctl

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

1. **Download `kubectl`:**
   Use `curl` to download the `kubectl` binary from the Amazon EKS S3 bucket. You can do this by running the following command in your terminal:
   ```bash
   curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
   ```


2. **Make the downloaded file executable:**
   After downloading `kubectl`, you need to make it executable using the `chmod` command:
   ```bash
   chmod +x ./kubectl
   ```

3. **Move `kubectl` to a directory in your PATH:**
   Now, move the `kubectl` binary to a directory that is included in your system's PATH environment variable. This ensures that you can run `kubectl` from any location in your terminal:
   ```bash
   sudo mv ./kubectl /usr/local/bin
   ```

4. **Verify the installation:**
   To confirm that `kubectl` has been installed correctly, you can check its version by running:
   ```bash
   kubectl version --short --client
   ```
   This command will print the client version of `kubectl`.
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1a8c6dc7-3337-4c82-9212-407ec2d3fb13)

After completing these steps, `kubectl` should be successfully installed on your Linux machine, and you can start using it to interact with Kubernetes clusters. 

# 4. Installation of EKSCTL

1. **Download `eksctl`:**
   Use `curl` to download the `eksctl` binary from the GitHub releases page. This command will download the latest version of `eksctl` for your operating system (Linux, MacOS, or Windows) and architecture (amd64 in this case).
   ```bash
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   ```

2. **Move `eksctl` to a directory in your PATH:**
   After downloading `eksctl`, move the `eksctl` binary from the `/tmp` directory to a directory that is included in your system's PATH environment variable. This ensures that you can run `eksctl` from any location in your terminal:
   ```bash
   sudo mv /tmp/eksctl /usr/local/bin
   ```

3. **Verify the installation:**
   To confirm that `eksctl` has been installed correctly, you can check its version by running:
   ```bash
   eksctl version
   ```
   This command will print the version of `eksctl`.
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/8ba11cd7-7cf2-4bbb-b366-6946becbb40d)

After completing these steps, `eksctl` should be successfully installed on your system, and you can start using it to manage Amazon EKS clusters. If you encounter 

# 5. Creation of EKS Cluster


### A. Creation of EKS Cluster
```
eksctl create cluster --name=my-eks92 \
                      --region=us-east-1 \
                      --zones=us-east-1a,us-east-1b \
                      --version=1.30 \
                      --without-nodegroup

```

1. `--name=my-eks92`: Specifies the name of the EKS cluster to be created. In this case, the cluster will be named "my-eks92".

2. `--region=us-east-1`: Specifies the AWS region in which the EKS cluster will be created. In this case, the region is "us-east-1", which corresponds to the US East (N. Virginia) region.

3. `--zones=us-east-1a,us-east-1b`: Specifies the availability zones within the chosen region where the EKS cluster's worker nodes will be deployed. Availability zones are distinct locations within a region that are engineered to be isolated from failures in other zones. Here, the cluster will use availability zones "us-east-1a" and "us-east-1b".

4. `--version=1.30`: Specifies the Kubernetes version for the EKS cluster. In this case, the cluster will be created with Kubernetes version 1.30.

5. `--without-nodegroup`: Indicates that no managed node group should be created along with the cluster. In Amazon EKS, a node group is a managed group of Amazon EC2 instances that are deployed to run Kubernetes pods. By using `--without-nodegroup`, you are instructing `eksctl` not to create any node group during the cluster creation process. You'll have to add one later manually or through another `eksctl` command.

Executing this command will create an Amazon EKS cluster named "my-eks92" in the "us-east-1" region, spanning availability zones "us-east-1a" and "us-east-1b", with Kubernetes version 1.30, and without creating any node group. You'll have an empty cluster ready to deploy applications once you add node groups to it.


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/ccb0417d-fda9-43fd-a89d-c808ec2fdee0)



After execution of EKS Cluster command

### b. To setup worker node
The `eksctl utils associate-iam-oidc-provider` command associates the IAM OIDC (OpenID Connect) provider for your Amazon EKS cluster with your AWS account. This association enables Kubernetes service accounts in your cluster to utilize AWS IAM roles for fine-grained access control to AWS services and resources.
```
eksctl utils associate-iam-oidc-provider \
    --region ap-south-1 \
    --cluster my-eks22 \
    --approve

```

Here's what each option in the command does:

- `--region ap-south-1`: Specifies the AWS region where your EKS cluster is located. In this case, it's the Asia Pacific (Mumbai) region (`ap-south-1`).
- `--cluster my-eks22`: Specifies the name of your EKS cluster. Replace `my-eks22` with the actual name of your cluster.
- `--approve`: Confirms the action without requiring any further confirmation from the user.

By running this command, you're granting permission for your EKS cluster to communicate with AWS IAM (Identity and Access Management) using OIDC. This allows Kubernetes service accounts within your cluster to assume IAM roles and access AWS resources securely.

After running this command, your EKS cluster will be associated with the IAM OIDC provider, and Kubernetes service accounts in the cluster can start assuming IAM roles for accessing AWS services.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/86429c03-ab6a-4bd6-a187-7b9cb9848f29)

### c. eksctl create nodegroup
```
eksctl create nodegroup --cluster=my-eks22 \
                       --region=ap-south-1 \
                       --name=node2 \
                       --node-type=t3.medium \
                       --nodes=3 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=20 \
                       --ssh-access \
                       --ssh-public-key=Key \
                       --managed \
                       --asg-access \
                       --external-dns-access \
                       --full-ecr-access \
                       --appmesh-access \
                       --alb-ingress-access
```

## Parameters

- `--cluster=my-eks22`: Specifies the name of the Amazon EKS cluster where the node group will be created.

- `--region=ap-south-1`: Specifies the AWS region where the EKS cluster is located.

- `--name=node2`: Specifies the name of the node group.

- `--node-type=t3.medium`: Specifies the instance type for the worker nodes.

- `--nodes=3`: Specifies the initial number of worker nodes to be launched.

- `--nodes-min=2`: Specifies the minimum number of worker nodes allowed in the node group.

- `--nodes-max=4`: Specifies the maximum number of worker nodes allowed in the node group.

- `--node-volume-size=20`: Specifies the size (in GB) of the EBS volume to be attached to each worker node.

- `--ssh-access`: Enables SSH access to the worker nodes.

- `--ssh-public-key=Key`: Specifies the SSH public key to be used for accessing the worker nodes.

- `--managed`: Indicates that the node group will be managed by Amazon EKS.

- `--asg-access`: Grants access to the Auto Scaling Group (ASG) associated with the node group.

- `--external-dns-access`: Grants access to ExternalDNS for managing DNS records.

- `--full-ecr-access`: Grants full access to Amazon ECR (Elastic Container Registry).

- `--appmesh-access`: Grants access to AWS App Mesh.

- `--alb-ingress-access`: Grants access to the ALB (Application Load Balancer) Ingress Controller.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/0370218a-6a6d-4bbb-9615-9af8a116f2a9)


