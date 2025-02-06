pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }
        
        stage('Execute Shell Script') {
            steps {
                sh 'chmod +x your-script.sh'   // Ensure script is executable
                sh './your-script.sh'         // Run the script
            }
        }
    }
}
