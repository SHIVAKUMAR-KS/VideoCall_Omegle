pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Images') {
            steps {
                script {
                    def command = 'cmd /c "docker-compose build"'
                    bat command // Use 'bat' for Windows
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    def command = 'cmd /c "docker-compose up -d"'
                    bat command
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def command = 'cmd /c "docker-compose down && docker-compose up -d"'
                    bat command
                }
            }
        }
    }
}
