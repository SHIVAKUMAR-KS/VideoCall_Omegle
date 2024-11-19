pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Build and Run Services') {
            steps {
                script {
                    bat 'docker-compose build'
                    bat 'docker-compose up -d'
                }
            }
        }
    }
}
