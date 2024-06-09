

### To check the status of a worker node in a cluster (commonly in environments like Kubernetes, Hadoop, or other distributed systems)

In Kubernetes, you can use `kubectl` to check the status of worker nodes.

```bash
kubectl get nodes
```

This command will list all nodes with their status. Look for the `STATUS` column to see if the nodes are `Ready` or `NotReady`.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/92480573-56e2-403a-a5f9-01787fc738d9)

### To modify the security group settings for an Amazon EKS (Elastic Kubernetes Service) cluster to allow all inbound traffic between master and worker nodes, you can follow these steps:

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

### Creation of Pipelines 

