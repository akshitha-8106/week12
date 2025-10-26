pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t registration:v1 .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'docker tag registration:v1 sriludone/registration:v1'
                sh 'docker push sriludone/registration:v1'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f D:/DevOps/week-2/deployment.yaml'
                sh 'kubectl apply -f D:/DevOps/week-2/service.yaml'
            }
        }
        stage('Automated UI Test') {
            steps {
                sh 'python D:/DevOps/week-2/test_registration.py'
            }
        }
    }
}
