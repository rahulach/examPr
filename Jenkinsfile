pipeline {
    agent { label 'built-in' } // This forces Jenkins to use your machine's environment where Docker & Minikube live

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-html-app:latest .'
            }
        }

        stage('Load Image to Minikube') {
            steps {
                sh 'minikube image load my-html-app:latest'
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