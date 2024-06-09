# Step 4 Create Service Account, Role & Assign that role, And create a secret for Service Account and geenrate a Token

## To check the status of a worker node in a cluster (commonly in environments like Kubernetes, Hadoop, or other distributed systems)

In Kubernetes, you can use `kubectl` to check the status of worker nodes.

```bash
kubectl get nodes
```

This command will list all nodes with their status. Look for the `STATUS` column to see if the nodes are `Ready` or `NotReady`.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/92480573-56e2-403a-a5f9-01787fc738d9)

## Open INBOUND TRAFFIC IN ADDITIONAL Security Group

### Step-by-Step Guide

1. **Open the Amazon EKS Console:**
   - Go to the [Amazon EKS console](https://console.aws.amazon.com/eks).

2. **Select Your Cluster:**
   - Click on the name of the EKS cluster you want to modify.

3. **Go to the Security Section:**
   - In the cluster details page, navigate to the `Networking` tab.
   - Look for the section that lists the security groups associated with the cluster.

4. **Identify the Security Group for Worker Nodes:**
   - Locate the security group that is used for the worker nodes. There will typically be one for the control plane (master nodes) and another for the worker nodes.

5. **Modify Inbound Rules:**
   - Click on the Security Group ID associated with the worker nodes to open the security group details in the EC2 console.

6. **Add Inbound Rule:**
   - In the security group details, go to the `Inbound rules` tab.
   - Click on the `Edit inbound rules` button.
   - Click `Add rule`.
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/e1a5ace8-fc08-4ed0-8bc1-7db65261d70c)

7. **Configure the Rule:**
   - Set `Type` to `All traffic`.
   - Set `Protocol` to `All`.
   - Set `Port range` to `All`.
   - In the `Source` field, select `Custom` and enter the security group ID of the master nodes or the worker nodes if the traffic should be allowed within the cluster.

8. **Save the Rule:**
   - Click `Save rules` to apply the changes.

To check the status of the resources in your Kubernetes cluster, you typically use the `kubectl get` command with specific resource types. If you're looking for names or status of different resources, here are some common commands:

### Check All Resources in a Namespace

```bash
kubectl get all -n <namespace>
```

This command will list all resources (pods, services, deployments, etc.) in the specified namespace.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/6e994428-42e2-4232-9eb6-088447054c32)

Creating a namespace in Kubernetes is a straightforward task that can be accomplished using the `kubectl` command-line tool. Below are the steps and commands to create a new namespace:

### Using `kubectl create namespace`

The simplest way to create a namespace is by using the `kubectl create namespace` command.

```bash
kubectl create namespace <namespace-name>
```

Replace `<namespace-name>` with the desired name for your namespace.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/51af6b0d-bee2-46ee-b19b-c2890d668d47)
