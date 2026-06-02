pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-html-app:latest .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl -- apply -f deployment.yaml'
                bat 'kubectl -- apply -f service.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl get pods'
                bat 'kubectl get svc'
            }
        }
    }
}