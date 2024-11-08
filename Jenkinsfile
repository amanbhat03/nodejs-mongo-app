pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = 'docker-compose'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the Git repository from GitHub
                git 'https://github.com/amanbhat03/nodejs-mongo-app.git'
            }
        }

        stage('Build and Deploy Containers') {
            steps {
                script {
                    // Build and deploy the Docker containers using docker-compose
                    sh 'docker-compose -f docker-compose.yml up --build -d'
                }
            }
        }

        stage('Test Containers') {
            steps {
                script {
                    // Check if containers are running
                    sh 'docker ps'
                }
            }
        }
    }

    post {
        always {
            // Clean up the containers after the pipeline finishes
            sh 'docker-compose down'
        }
    }
}
