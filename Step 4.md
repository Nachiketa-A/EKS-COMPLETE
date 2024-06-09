# Step 4 Create Service Account, Role & Assign that role, And create a secret for Service Account and geenrate a Token

## To check the status of a worker node in a cluster (commonly in environments like Kubernetes, Hadoop, or other distributed systems)

In Kubernetes, you can use `kubectl` to check the status of worker nodes.

```bash
kubectl get nodes
```

This command will list all nodes with their status. Look for the `STATUS` column to see if the nodes are `Ready` or `NotReady`.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/92480573-56e2-403a-a5f9-01787fc738d9)

# 1. Open INBOUND TRAFFIC IN ADDITIONAL Security Group

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

# 2. Creating Service Account

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: jenkins
  namespace: webapps
```

### Breakdown of the YAML File

#### `apiVersion: v1`
- **Explanation:** This specifies the version of the Kubernetes API that you are using to create this object. `v1` is a stable version of the API that includes core resources such as `ServiceAccount`.

#### `kind: ServiceAccount`
- **Explanation:** This specifies the type of Kubernetes object you are creating. In this case, it is a `ServiceAccount`.

#### `metadata`
- **Explanation:** The `metadata` section provides standard information about the object, such as its name, namespace, labels, and annotations.

##### `name: jenkins`
- **Explanation:** This sets the name of the `ServiceAccount`. Here, the name is `jenkins`.

##### `namespace: webapps`
- **Explanation:** This specifies the namespace in which the `ServiceAccount` will be created. A namespace in Kubernetes is a way to divide cluster resources between multiple users (via resource quota). In this case, the `ServiceAccount` will be created in the `webapps` namespace.

### Purpose of a ServiceAccount

A `ServiceAccount` in Kubernetes is used to provide an identity to pods running in a cluster. When a pod runs in the cluster, it can use this `ServiceAccount` to interact with the Kubernetes API server and other services securely. Each pod inherits the permissions of the `ServiceAccount` it's associated with.

To create a YAML file using the `vi` editor, add the `ServiceAccount` definition, and then apply it using `kubectl`, follow these steps:

### Step-by-Step Instructions

1. **Open `vi` editor to create a new file:**

   ```bash
   vi batman.yml
   ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/017edfa5-9076-4246-949e-01701d24f34d)

2. **Add the `ServiceAccount` definition to the file:**

   Press `i` to enter insert mode and paste the following content:

   ```yaml
   apiVersion: v1
   kind: ServiceAccount
   metadata:
     name: jenkins
     namespace: webapps
   ```

3. **Save and exit the `vi` editor:**

   - Press `Esc` to exit insert mode.
   - Type `:wq` and press `Enter` to save and quit `vi`.

4. **Create the namespace if it doesn't already exist:**

   ```bash
   kubectl create namespace webapps
   ```

5. **Apply the YAML file to create the `ServiceAccount`:**

   ```bash
   kubectl apply -f batman.yml
   ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/aed79d1a-903f-4159-9417-112ca8cbbcb7)

### Verification

To verify that the `ServiceAccount` has been created successfully, list the service accounts in the `webapps` namespace:

```bash
kubectl get serviceaccounts -n webapps
```

#### Example output:

```
NAME      SECRETS   AGE
default   1         10d
jenkins   1         1m
```

This output confirms that the `jenkins` `ServiceAccount` has been created in the `webapps` namespace.

# 3. Create a Role
```

apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: app-role
  namespace: webapps
rules:
  - apiGroups:
        - ""
        - apps
        - autoscaling
        - batch
        - extensions
        - policy
        - rbac.authorization.k8s.io
    resources:
      - pods
      - secrets
      - componentstatuses
      - configmaps
      - daemonsets
      - deployments
      - events
      - endpoints
      - horizontalpodautoscalers
      - ingress
      - jobs
      - limitranges
      - namespaces
      - nodes
      - pods
      - persistentvolumes
      - persistentvolumeclaims
      - resourcequotas
      - replicasets
      - replicationcontrollers
      - serviceaccounts
      - services
    verbs: ["get", "list", "watch", "create", "update", "patch", "delete"]
```

This YAML defines a Role resource in Kubernetes RBAC (Role-Based Access Control). 

- **apiVersion**: Specifies the version of the Kubernetes API that you are using for this object. In this case, it's `rbac.authorization.k8s.io/v1`, indicating Kubernetes RBAC API version 1.

- **kind**: Defines the type of Kubernetes resource you are creating. Here, it's a `Role`.

- **metadata**: Provides standard metadata about the object, such as its name and namespace.

  - **name**: Sets the name of the Role as `app-role`.
  
  - **namespace**: Specifies the namespace in which the Role will be created. In this case, it's `webapps`.

- **rules**: Defines the permissions associated with this Role. The `rules` section specifies the resources and the corresponding verbs allowed for those resources.

  - **apiGroups**: Indicates the API groups for which these rules apply. In this case, it includes an empty string `""` (core API group) and several other groups like `apps`, `autoscaling`, `batch`, etc.
  
  - **resources**: Lists the Kubernetes resources that these rules apply to. It includes a wide range of resources like `pods`, `secrets`, `deployments`, etc.
  
  - **verbs**: Specifies the actions allowed on the listed resources. The actions include `get`, `list`, `watch`, `create`, `update`, `patch`, and `delete`.

