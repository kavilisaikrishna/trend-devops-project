pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "saikrishna0926/trend-app-docker:latest"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/kavilisaikrishna/trend-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }

    }
}
