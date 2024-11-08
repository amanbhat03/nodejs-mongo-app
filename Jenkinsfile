pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = 'docker-compose'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/amanbhat03/nodejs-mongo-app.git'
            }
        }

        stage('Build and Deploy Containers') {
            steps {
                script {
                    sh 'docker-compose -f docker-compose.yml up --build -d'
                }
            }
        }

        stage('Test Containers') {
            steps {
                script {
                    sh 'docker ps'
                }
            }
        }
    }

    post {
        always {
            sh 'docker-compose down'
        }
    }
}
