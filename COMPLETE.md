
## What is this Application:- 

**Online Boutique** is a demo e-commerce application designed to showcase how different parts of a web-based store can be built using a cloud-first microservices architecture. Microservices mean that the application is divided into smaller, independently deployable services, each handling a specific part of the application's functionality.

The application consists of 11 separate services (or microservices), each written in different programming languages and responsible for different tasks:

1. **frontend** (Go): This is the main web server that shows the website to users. It doesn't need users to sign up or log in; it creates session IDs automatically.

2. **cartservice** (C#): Manages the shopping cart. It saves items in the cart using Redis, a type of database, and retrieves them when needed.

3. **productcatalogservice** (Go): Provides the product list from a JSON file, allows searching for products, and fetching details of individual products.

4. **currencyservice** (Node.js): Converts prices between different currencies using real exchange rates from the European Central Bank. This service handles the highest number of requests per second.

5. **paymentservice** (Node.js): Processes payments by taking credit card information (simulated) and returning a transaction ID.

6. **shippingservice** (Go): Estimates shipping costs based on the items in the shopping cart and provides shipping services (simulated).

7. **emailservice** (Python): Sends order confirmation emails to users (simulated).

8. **checkoutservice** (Go): Manages the checkout process. It collects the items in the cart, prepares the order, processes the payment, handles shipping, and sends the confirmation email.

9. **recommendationservice** (Python): Suggests other products to users based on what's in their shopping cart.

10. **adservice** (Java): Displays text advertisements based on certain keywords.

11. **loadgenerator** (Python/Locust): Simulates real user activity on the website by continuously sending requests to the frontend.

Each of these services is like a small, independent piece of the overall application. They work together to create the full shopping experience for users but can be developed, deployed, and scaled independently.

```
```
# 1. First Create a user in AWS IAM with any name
To set up an EKS (Amazon Elastic Kubernetes Service) account without using the root account, it's indeed a best practice to create a new IAM (Identity and Access Management) user with limited access. Here's a step-by-step guide to creating an IAM user and attaching the necessary policies, including creating a custom policy.

### Step-by-Step Guide

1. **Log in to the AWS Management Console with Root Account**
   - Use your root account to log in to the AWS Management Console.

2. **Navigate to IAM**
   - In the AWS Management Console, search for and select **IAM** (Identity and Access Management).

3. **Create a New IAM User**
   - Go to **Users** in the IAM dashboard.
   - Click on **Add user**.

4. **Configure User Details**
   - Enter the user name (e.g., `eks-admin`).
   - Select **AWS Management Console access**.
   - Choose **Custom password**, set the initial password, and optionally require the user to create a new password at the next sign-in.

5. **Set Permissions**
   - Select **Attach policies directly**.
   - Attach the following AWS managed policies:
     - `AmazonEC2FullAccess`
     - `AmazonEKS_CNI_Policy`
     - `AmazonEKSClusterPolicy`
     - `AmazonEKSWorkerNodePolicy`
     - `AWSCloudFormationFullAccess`
     - `IAMFullAccess`

6. **Create and Attach a Custom Policy**
   - Click on **Create policy**.
   - Select the **JSON** tab and enter the following policy content:
     ```json
     {
         "Version": "2012-10-17",
         "Statement": [
             {
                 "Sid": "VisualEditor0",
                 "Effect": "Allow",
                 "Action": "eks:*",
                 "Resource": "*"
             }
         ]
     }
     ```
   - Click on **Next: Tags** (you can skip adding tags).
   - Click on **Next: Review**.
   - Provide a name for the policy (e.g., `EKSPolicy`).
   - Click on **Create policy**.

7. **Attach the Custom Policy to the User**
   - Go back to the **Users** section.
   - Select the user you created (e.g., `eks-admin`).
   - Go to the **Permissions** tab.
   - Click on **Add permissions**.
   - Choose **Attach policies directly**.
   - Search for and select the custom policy you created (`EKSPolicy`).
   - Click on **Next: Review**.
   - Click on **Add permissions**.

8. **Review and Finish**
   - Ensure the user has the following policies attached:
     - `AmazonEC2FullAccess`
     - `AmazonEKS_CNI_Policy`
     - `AmazonEKSClusterPolicy`
     - `AmazonEKSWorkerNodePolicy`
     - `AWSCloudFormationFullAccess`
     - `IAMFullAccess`
     - `EKSPolicy`
![Policies](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/e51ae215-72c6-4d61-b5d6-2c925c454053)

# 2. Creating an EC2 instance for Jenkins using the AWS Management Console:

1. **Log in to the AWS Management Console**
   - Open your web browser and go to the AWS Management Console.
   - Log in with your IAM user credentials.

2. **Navigate to EC2**
   - In the AWS Management Console, search for and select **EC2** to open the EC2 Dashboard.

3. **Launch Instance**
   - Click on the **Launch instance** button.

4. **Configure the Instance**
   - **Name and tags**:
     - Add a name: `jenkins`
   
   - **Application and OS Images (Amazon Machine Image)**:
     - Choose **Ubuntu** as the operating system. Select the latest stable version of Ubuntu.
   
   - **Instance type**:
     - Select **t2.xlarge**.

5. **Key Pair (Login)**
   - **Create a new key pair**:
     - Click on **Create a new key pair**.
     - Enter a key pair name (e.g., `jenkins-keypair`).
     - Select **Key pair type**: RSA
     - Select **Private key file format**: `.pem` (for use with OpenSSH).
     - Click **Create key pair**.
     - The key pair file (`.pem`) will be automatically downloaded. Keep this file safe, as you will need it to SSH into your instance.

6. **Network settings**
 
![image](https://github.com/Nachiketa-A/EKS-COMPLETE/assets/157089767/685912be-d083-4858-9355-1e26de533cdc)


7. **Configure storage**
   - Change the **Size (GiB)** to `30` for the root volume.

8. **Advanced details**
   - Click on **Launch instance**.

9. **Wait for the Instance to Launch**
   - It will take a few minutes for the instance to be up and running.
   - You can monitor the status in the **Instances** section of the EC2 Dashboard.


To connect to your new EC2 instance using MobaXterm and resolve the "Network error: Connection timed out" issue, follow these steps:

### Step 1: Add an SSH Inbound Rule to the Security Group

To avoid this error while using Mobaxtreme

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1d375f07-e5f4-458e-8638-4e6f04afddf5)

1. **Log in to the AWS Management Console**:
   - Open the AWS Management Console and log in with your IAM user credentials.

2. **Navigate to EC2**:
   - In the AWS Management Console, search for and select **EC2** to open the EC2 Dashboard.

3. **Select Your Instance**:
   - In the EC2 Dashboard, click on **Instances** in the left-hand menu.
   - Select the instance you named `jenkins`.

4. **Modify the Security Group**:
   - In the instance details at the bottom, find and click on the **Security groups** link associated with your instance.
   - This will take you to the Security Groups section.

5. **Add an SSH Rule**:
   - Select the security group linked to your instance.
   - Click on the **Inbound rules** tab.
   - Click on **Edit inbound rules**.
   - Click **Add rule**.
     - **Type**: SSH
     - **Protocol**: TCP
     - **Port range**: 22
     - **Source**: Custom (or choose "My IP" to allow access from your IP only)
     - **Custom IP**: Enter `0.0.0.0/0` to allow all IP addresses (not recommended for production due to security risks) or specify a more restrictive IP range.
   


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/2aaa4cb9-7be3-4719-86bf-4276d7baaf25)



![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/8bea75fd-d1dd-42fc-a01f-f611a27fd80d)



![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/66db0f4c-5687-41eb-9544-67517662935b)


Click on **Save Rules**

### Step 2: Connect Using MobaXterm

1. **Download and Install MobaXterm**:
   - If you haven't already, download and install MobaXterm from the official website: [MobaXterm](https://mobaxterm.mobatek.net/).

2. **Open MobaXterm**:
   - Launch MobaXterm on your computer.

3. **Start a New SSH Session**:
   - Click on the **Session** icon in the top left corner.
   - Select **SSH**.

4. **Configure the SSH Session**:
   - **Remote host**: Enter the public IP address or DNS of your EC2 instance. You can find this in the EC2 instance details under the "Public IPv4 address" or "Public DNS (IPv4)".
   - **Specify username**: Enter `ubuntu` (the default username for Ubuntu AMIs).
   - **Port**: 22

5. **Advanced SSH Settings**:
   - Click on **Advanced SSH settings**.
   - **Use private key**: Select this option and browse to the location of your `.pem` key file you downloaded earlier (`jenkins-keypair.pem`).

6. **Start the Session**:
   - Click on **OK** to start the session.

### Troubleshooting

- **Ensure Instance is Running**: Make sure your EC2 instance is in the `running` state.
- **Check Network Configuration**: Verify that your instance's security group has the correct inbound rules allowing SSH access from your IP.
- **Correct Key Permissions**: Ensure your private key file (`.pem`) has the correct permissions. It should be readable only by you. You can change the permissions on your local machine by running `chmod 400 jenkins-keypair.pem` in a terminal if you're using a Unix-based system.

By following these steps, you should be able to connect to your EC2 instance using MobaXterm and resolve any network timeout issues related to SSH access.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/4881d1bf-e259-4d2f-8465-1ee496e67a1d)

Click on **session**
click on **SSH**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/aa15c01f-b2c9-48f8-969b-a7314a213cdf)



![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/b053feed-93c2-4a59-8e96-78e0689f3327)

coneection successfull






