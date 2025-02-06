pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/mohshaamil/trivvy.git'
            }
        }
        
        stage('Execute Shell Script') {
            steps {
                sh 'chmod +x website.sh'   // Ensure script is executable
                sh './website.sh'         // Run the script
            }
        }
    }
}
