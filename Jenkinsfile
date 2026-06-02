pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'eval $(minikube -p minikube docker-env) && docker build -t my-html-app:latest .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}