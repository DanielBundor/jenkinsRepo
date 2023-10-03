pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'docker build -t my-app .'
            }
        }
        
        stage('Test') {
            steps {
                sh 'docker run my-app test'
            }
        }
        
        stage('Deploy Staging') {
            steps {
                sh 'docker-compose -f docker-compose.staging.yml up -d'
            }
        }
    }

    post {
        success {
            echo 'Deployment to staging successful!'
        }
    }
}

