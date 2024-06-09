
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

9. **Sign in with the New User**
   - Provide the new user with their sign-in URL, username, and password.
   - The new user can now sign in to the AWS Management Console with the appropriate permissions to manage EKS.

By following these steps, you've created a new IAM user with limited access necessary to manage EKS resources, adhering to AWS best practices for security and access control.
# Connecting Instance with MobaXterm

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/4881d1bf-e259-4d2f-8465-1ee496e67a1d)

Click on **session**
click on **SSH**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/aa15c01f-b2c9-48f8-969b-a7314a213cdf)


After clickin on **ok** you will get on error

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1d375f07-e5f4-458e-8638-4e6f04afddf5)

To resolve this error 

Go to **EC2 instance**

Click on **SEcurity Group**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/2aaa4cb9-7be3-4719-86bf-4276d7baaf25)

Click on **Edit inbound rules**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/8bea75fd-d1dd-42fc-a01f-f611a27fd80d)

**Add rules**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/66db0f4c-5687-41eb-9544-67517662935b)

Click on **Save Rules**

Again go to MobaXterm and Press **R** to restart the session

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/b053feed-93c2-4a59-8e96-78e0689f3327)

coneection successfull






