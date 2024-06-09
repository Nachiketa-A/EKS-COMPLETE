# Step 3. Configuration of Jenkins

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


# Installing the mentioned plugins in Jenkins:

1. **SonarQube Scanner Plugin:**
   - Navigate to "Manage Jenkins" > "Manage Plugins" > "Available" tab.
   - Search for "SonarQube Scanner".
   - Check the checkbox next to the "SonarQube Scanner" plugin.
   - Click "Install without restart".

2. **Docker Plugin:**
   - Go to "Manage Jenkins" > "Manage Plugins" > "Available" tab.
   - Search for "Docker".
   - Check the checkbox next to the "Docker Pipeline" plugin.
   - Click "Install without restart".

3. **Docker Pipeline Plugin:**
   - Follow the same steps as for the Docker plugin, searching for "Docker Pipeline" instead.

4. **Docker Build Step Plugin:**
   - Similar to the previous steps, search for "Docker Build Step".
   - Check the checkbox next to the plugin.
   - Click "Install without restart".

5. **Kubernetes Plugin:**
   - Search for "Kubernetes".
   - Check the checkbox next to the "Kubernetes CLI" plugin.
   - Click "Install without restart".

6. **CodeBees Docker Build and Publish Plugin:**
   - Search for "CodeBees Docker Build and Publish".
   - Check the checkbox next to the plugin.
   - Click "Install without restart".

7. **Kubernetes CLI Plugin:**
   - Search for "Kubernetes CLI".
   - Check the checkbox next to the plugin.
   - Click "Install without restart".

After installing these plugins, you'll have the necessary tools integrated into Jenkins for managing Docker containers, building Docker images, scanning code with SonarQube, and working with Kubernetes. You can configure and use them in your Jenkins pipelines as needed.![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/3f4e1429-937c-4781-b105-195126bb875a)


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/0cd60108-c6ec-4fcb-93ac-f91aea392a2d)


![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/238cdf38-0b7e-44f9-a78b-8d6b6bcf6820)


# Configuration 

To configure Jenkins with Docker and SonarQube Scanner, follow these steps:

1. **Manage Jenkins:**
   - Navigate to your Jenkins dashboard.
   - Click on "Manage Jenkins" from the left-hand side menu.

2. **Install Docker:**
   - Click on "Tools".
   - Look for an option to manage tool installations. It might be labeled as "Global Tool Configuration" or similar.
   - Find the section for Docker and Docker versions.
   - Add the latest Docker version by specifying its name and selecting the "Latest" version if available. Make sure you have Docker installed on the Jenkins server for this step to work correctly.
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/ac8543a0-43ff-46d0-9cb8-ed709b976c69)

3. **SonarQube Scanner:**
   - Still in the "Manage Jenkins" section, look for a similar tool configuration option.
   - Find the section for SonarQube Scanner.
   - Add a new SonarQube Scanner configuration by giving it a name, such as "sonar-scanner".
   - Check the box to "Install automatically" if available.
   - Specify the desired version, such as "6.0.xx".
![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/89de3cc7-9b21-4bda-949d-05a3adaed0c4)

4. **Save Configuration:**
   - After adding Docker and SonarQube Scanner configurations, make sure to save the changes.

These steps should enable Jenkins to use Docker and SonarQube Scanner in your pipeline jobs. Make sure that Docker is properly installed on the Jenkins server, and SonarQube Scanner is accessible. Adjust the configuration as needed based on your Jenkins setup and requirements.


To configure Sonarqube server

Go to Sonarqube -> Administartion -> security -> users -> token

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/a79251d0-f192-402d-81a3-014e0fcde940)

Copy token 

Go to Jenkins -> manage jenkins -> credentials-> system -> global credentials -> add credentials

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/c5730c06-d3f1-4f0d-b591-53c83e519e71)

To add sonarqube server to the jenkins

MAnage jenkins -> system

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1e992fd4-0079-4102-8f2e-27273acd4926)



