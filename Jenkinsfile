pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                // Ensure the repo is cloned correctly
                checkout scm
            }
        }
        stage('Validate Workspace') {
            steps {
                script {
                    bat 'dir /s'
                }
            }
        }
        stage('Build Docker Images') {
            steps {
                script {
                    bat 'docker-compose build'
                }
            }
        }
        stage('Run Docker Containers') {
            steps {
                script {
                    bat 'docker-compose up -d'
                }
            }
        }
    }
}
