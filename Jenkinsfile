pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "harshinimdocker/trend-app"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:latest .'
            }
        }

        stage('Push Docker Image to DockerHub') {
            steps {
                sh 'docker push $DOCKER_IMAGE:latest'
            }
        }

        stage('Deploy to Kubernetes (EKS)') {
            steps {
                sh 'kubectl apply -f deployment.yml' 
                sh 'kubectl apply -f service.yml' 
            }
        }

    }

    post {
        success {
            echo 'Application successfully deployed!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
