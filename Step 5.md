# Jenkins Pipeline Creation

This guide provides a step-by-step process for creating a new pipeline in Jenkins.

## Steps to Create a New Pipeline

### 1. Navigate to Jenkins Dashboard
Open your Jenkins dashboard in your web browser.

### 2. Create a New Item
- Click on the **"New Item"** link on the left-hand menu.

### 3. Enter Item Name
- In the **"Enter an item name"** field, type the desired name for your pipeline.

### 4. Select Pipeline
- Choose the **"Pipeline"** option from the list of item types.

### 5. Click OK
- Click the **"OK"** button to proceed.

### 6. Configure the Pipeline
- Configure your pipeline.

![image](https://github.com/Nachiketa-A/Microservice_App/assets/157089767/d764b10a-5696-43b1-835d-0136fb4e6ded)

## Additional Configuration

Once the pipeline is created, you can further configure it by adding your pipeline script in the configuration section. This script can define the stages and steps of your pipeline.

### Pipeline Script

Here is a pipeline script:

```groovy
pipeline {
    agent any
    
    environment {
        
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'latest', url: 'https://github.com/jaiswaladi246/10-Tier-MicroService-Appliction.git'
            }
        }
        
        stage('SonarQube') {
            steps {
                
                withSonarQubeEnv('sonar') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=. '''
                }
               
            }
        }
        
        stage('adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/adservice/') {
                                 sh "docker build -t nachia2024/adservice:latest ."
                                 sh "docker push nachia2024/adservice:latest"
				 sh " docker rmi nachia2024/adservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('cartservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src/') {
                                 sh "docker build -t nachia2024/cartservice:latest ."
                                 sh "docker push nachia2024/cartservice:latest"
				 sh " docker rmi nachia2024/cartservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('checkoutservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice/') {
                                 sh "docker build -t nachia2024/checkoutservice:latest ."
                                 sh "docker push nachia2024/checkoutservice:latest"
				 sh " docker rmi nachia2024/checkoutservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('currencyservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/currencyservice/') {
                                 sh "docker build -t nachia2024/currencyservice:latest ."
                                 sh "docker push nachia2024/currencyservice:latest"
				 sh " docker rmi nachia2024/currencyservice:latest"
                        }
                    }
                }
            }
        }
        
		stage('emailservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/emailservice/') {
                                 sh "docker build -t nachia2024/emailservice:latest ."
                                 sh "docker push nachia2024/emailservice:latest"
				 sh " docker rmi nachia2024/emailservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('frontend') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/frontend/') {
                                 sh "docker build -t nachia2024/frontend:latest ."
                                 sh "docker push nachia2024/frontend:latest"
				 sh " docker rmi nachia2024/frontend:latest"
                        }
                    }
                }
            }
        }
		
		stage('loadgenerator') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator/') {
                                 sh "docker build -t nachia2024/loadgenerator:latest ."
                                 sh "docker push nachia2024/loadgenerator:latest"
				 sh " docker rmi nachia2024/loadgenerator:latest"
                        }
                    }
                }
            }
        }
		
		stage('paymentservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/paymentservice/') {
                                 sh "docker build -t nachia2024/paymentservice:latest ."
                                 sh "docker push nachia2024/paymentservice:latest"
				 sh " docker rmi nachia2024/paymentservice:latest"
                        }
                    }
                }
            }
        }
        
		stage('productcatalogservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice/') {
                                 sh "docker build -t nachia2024/productcatalogservice:latest ."
                                 sh "docker push nachia2024/productcatalogservice:latest"
				 sh " docker rmi nachia2024/productcatalogservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('recommendationservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice/') {
                                 sh "docker build -t nachia2024/recommendationservice:latest ."
                                 sh "docker push nachia2024/recommendationservice:latest"
				 sh " docker rmi nachia2024/recommendationservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('shippingservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/shippingservice/') {
                                 sh "docker build -t nachia2024/shippingservice:latest ."
                                 sh "docker push nachia2024/shippingservice:latest"
				 sh " docker rmi nachia2024/shippingservice:latest"
                        }
                    }
                }
            }
        }
        
        
        	stage('K8-Deploy') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my-eks8', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://2BCD568E04EC6456125F85067AFE81B9.gr7.us-east-1.eks.amazonaws.com') {
                         sh 'kubectl apply -f deployment-service.yml'
                         sh 'kubectl get pods '
                         sh 'kubectl get svc'
                }
            }
        }
        
    }
}

