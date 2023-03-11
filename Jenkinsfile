pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-test .'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker login -u amitow -p Mminani029'
                sh 'docker tag my-test amitow/test/my-test:latest'
                sh 'docker push amitow/test:my-test'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yml'
                sh 'kubectl apply -f service.yml'
            }
        }
    }
}

