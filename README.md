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


## [Step 1. Creation of user for EKS and Instance for Jenkins](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%201.md)

1. [First Create a user in AWS IAM](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%201.md#1-first-create-a-user-in-aws-iam-with-any-name)
2. [Creating an EC2 instance for Jenkins using the AWS Management Console](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%201.md#2-creating-an-ec2-instance-for-jenkins-using-the-aws-management-console)

## [Step 2. Installation and Configuration of AWS CLI, Kubectl, Eksctl](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%202.md)

1. [Installation of AWS CLI](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%202.md#1-installation-of-aws-cli)
2. [Create access keys for your IAM user and configure the AWS](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%202.md#2-create-access-keys-for-your-iam-user-and-configure-the-aws)
3. [Install kubectl](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%202.md#3-install-kubectl)
4. [Installation of EKSCTL](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%202.md#4-installation-of-eksctl)
5. [Creation of EKS Cluster](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%202.md#5-creation-of-eks-cluster)

## [Step 3. Configuration of Jenkins](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%203.md)
1. [Install OpenJDK 17](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%203.md#1-install-openjdk-17)
2. [Installing Jenkins from the Jenkins Debian repository with the GPG key](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%203.md#2-installing-jenkins-from-the-jenkins-debian-repository-with-the-gpg-key)
3. [Installation of sonarqube using Docker](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%203.md#installing-the-mentioned-plugins-in-jenkins)
4. [Installing the mentioned plugins in Jenkins](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%203.md#installing-the-mentioned-plugins-in-jenkins)

## [Step 4 Create Service Account, Role & Assign that role, And create a secret for Service Account and geenrate a Token](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%204.md#step-4-create-service-account-role--assign-that-role-and-create-a-secret-for-service-account-and-geenrate-a-token)

1. [Open INBOUND TRAFFIC IN ADDITIONAL Security Group]
2. [Creating Service Account]
3. [Create a Role]
4. [Bind the role to service account]
5. [To create a token for service account use below yaml file]

## [Step 5 Jenkins Pipeline Creation ]

1. [New Pipeline Creation](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%205.md#steps-to-create-a-new-pipeline)
2. [Pipeline Script Creation](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%205.md#pipeline-script)
3. [Build and verify the Ppipeline](https://github.com/Nachiketa-A/EKS-COMPLETE/blob/main/Step%205.md#build-and-verify-the-pipeline)
