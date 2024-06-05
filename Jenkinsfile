pipeline {
    agent any  // This specifies that Jenkins can run this pipeline on any available agent

    environment {
        DOCKER_HUB_CREDENTIALS_ID = '12345678'  // ID of your Docker Hub credentials stored in Jenkins
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url:'https://github.com/Sohaib-Ahmed869/exam.git'
            }
        }

        stage('Build and Push Docker Images') {
            steps {
                script {
                    // Login to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS_ID) {
                        // Build the Docker images
                        sh 'docker-compose build'
                        // Push the Docker images to Docker Hub
                        sh 'docker-compose push'
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up Docker images and resources after building and pushing
            sh 'docker-compose down --rmi all'
        }
    }
}
