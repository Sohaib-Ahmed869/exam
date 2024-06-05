pipeline {
    agent any  // This specifies that Jenkins can run this pipeline on any available agent

    environment {
        DOCKER_HUB_CREDENTIALS_ID = '12345678'  // ID of your Docker Hub credentials stored in Jenkins
    }

    stages {
        stage('21i-1114 Checkout Code') {
            steps {
                git branch: 'master', url:'https://github.com/Sohaib-Ahmed869/exam.git'
            }
        }

        stage('21i-1114 Build and Push Docker Images') {
            steps {
                script {
                    // Login to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS_ID) {
                        // Build the Docker images
                        bat 'docker-compose build'
                        // Push the Docker images to Docker Hub
                        bat 'docker-compose push'
                    }
                }
            }
        }
    }
}
