# 

# 1. Install OpenJDK 17

1 . **Install OpenJDK 17 Headless:**
   OpenJDK is an open-source implementation of the Java Platform. The "headless" version means it doesn't include graphical user interface (GUI) libraries.
   ```bash
   sudo apt install openjdk-17-jdk-headless
   ```

2. **Verify Installation:**
   After the installation is complete, you can verify that Java 17 is installed by checking the version:
   ```bash
   java -version
   ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/8df7e31e-3d27-461e-a45d-e5051a324c92)

# 2. Installing Jenkins from the Jenkins Debian repository with the GPG key

1. **Download Jenkins GPG Key:**
   This command downloads the Jenkins GPG key and saves it to `/usr/share/keyrings/jenkins-keyring.asc`. GPG keys are used to verify the authenticity of packages.
   ```bash
   sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
   https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
   ```

2. **Add Jenkins Repository to APT Sources:**
   This command adds the Jenkins Debian repository to the list of APT sources, which allows `apt-get` to find and install Jenkins packages. It uses the downloaded GPG key to verify the repository.
   ```bash
   echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
   https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null
   ```

3. **Update APT Package Index:**
   This command updates the local package index to ensure that the latest package information is available.
   ```bash
   sudo apt-get update
   ```

4. **Install Jenkins:**
   Finally, this command installs Jenkins using `apt-get`.
   ```bash
   sudo apt-get install jenkins
   ```

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/f2537ec8-1009-472e-83cb-930844a2b5ba)

To access Jenkins copy te public ip address and open it on port 8080

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/b6800bb8-2286-4333-a0c7-8bf8ffd79f09)

To get the password of jenkins use below command


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/a6411405-a062-45b5-b4f2-86ba374c45f7)

One pop up is coming click on **Install sugested Plugin**

Credentials of jenkins

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/ff770f0f-26b0-4092-a309-ebfed77323da)


# 3. Installation of sonarqube using Docker

To set up SonarQube using Docker, you can follow these steps:

1. **Install Docker:**
   If Docker is not already installed on your system, you can install it using the following command:
   ```bash
   sudo apt install docker.io
   ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/50bb3fa6-e5fc-4768-8003-284f7eef0f5e)

2. **Change Permissions (Optional):**
   It's not recommended to change permissions on system files like `docker.sock`. Docker commands typically require sudo privileges or being a member of the docker group. However, if you want to grant more permissive permissions, you can use the following command (though it's not recommended):
   ```bash
   sudo chmod 777 /var/run/docker.sock
   ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/813b4e0c-b8b7-4a4d-8f84-91db780dadad)

3. **Pull and Run SonarQube Container:**
   Now, you can pull and run the SonarQube Docker container. There is a minor correction in your command. It should be:
   ```bash
   docker run -d -p 9000:9000 sonarqube:lts-community
   ```
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/dc5e970e-986b-4862-83d2-12f0a3ac1475)

   This command will download the SonarQube Community Edition Docker image (`sonarqube:lts-community`) and run it in detached mode (`-d`). It exposes port 9000 of the container to port 9000 on the host (`-p 9000:9000`), allowing you to access SonarQube from your browser.

After executing these steps, SonarQube should be running and accessible at `http://localhost:9000`. You can then configure it according to your needs and start analyzing code.

### Command to check container is created or not

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/a68323ee-f4e7-4630-9064-11a3cb08b7bc)

Now, To access sonarqube copy te public ip address and open it on port 9000

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/2733db19-184d-45f1-84c2-fc6da25cd2d7)

### Use Default sonarqube credentials (admin )

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1504417b-6bec-4e60-a323-b902809979ab)


After execution of EKS Cluster command

To setup worker node

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/86429c03-ab6a-4bd6-a187-7b9cb9848f29)


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/0370218a-6a6d-4bbb-9615-9af8a116f2a9)


Meanwhhile we will manage jenkins

**Steps**

Go to **manage Jenkins**

click **Plugins**

click on **Available Plugins**

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/3f4e1429-937c-4781-b105-195126bb875a)

For docker Plugins

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/0cd60108-c6ec-4fcb-93ac-f91aea392a2d)

For kubernetes plugins

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/238cdf38-0b7e-44f9-a78b-8d6b6bcf6820)

Click **Install**










![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1504417b-6bec-4e60-a323-b902809979ab)
