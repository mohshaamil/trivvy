pipeline {
    agent any
     
    environment {
    REGISTRY_NAME = "mohshaamacr"
    ACR_LOGIN_SERVER = "${mohshaamacr}.azurecr.io"
    REPOSITORY_NAME = "html-example"
    }
    stages { 
        stage('SCM Checkout') {
            steps{
           git branch: 'main', url: 'https://github.com/mohshaamil/trivvy.git'
            }
        }
        
       // Building Docker Image 
       stage ('Build Docker image') {
        steps {
                script {
                 sh "docker build -t ${REGISTRY_NAME}.azurecr.io/${REPOSITORY_NAME}:$BUILD_NUMBER ." 
                }
            }
       }

    // Uploading Docker images into ACR
        stage('Upload Image to ACR') {
         steps{   
             script {
               withCredentials([usernamePassword(credentialsId: 'acr-credentials', usernameVariable: 'SERVICE_PRINCIPAL_ID', passwordVariable: 'SERVICE_PRINCIPAL_PASSWORD')]) {
     sh "docker login ${ACR_LOGIN_SERVER} -u $SERVICE_PRINCIPAL_ID -p $SERVICE_PRINCIPAL_PASSWORD"
                 sh " docker push ${REGISTRY_NAME}.azurecr.io/${REPOSITORY_NAME}:$BUILD_NUMBER"
                  }
              }
         }
      }
   }
}
