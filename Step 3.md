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

installation of docker

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/50bb3fa6-e5fc-4768-8003-284f7eef0f5e)

command to access all docker permissions

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/813b4e0c-b8b7-4a4d-8f84-91db780dadad)

Command to set up sonarqube

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/dc5e970e-986b-4862-83d2-12f0a3ac1475)

-d : Detached mode (it will run the logs in background)

-p : mention te port range

eg: 9000:9001 (9000 is a host port ; 9001 is  container port)

lts: latest versuion of sonarqube image

command to check container is created or not

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/a68323ee-f4e7-4630-9064-11a3cb08b7bc)

To access sonarqube copy te public ip address and open it on port 9000

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/2733db19-184d-45f1-84c2-fc6da25cd2d7)

sonarqube credentials

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/1504417b-6bec-4e60-a323-b902809979ab)
