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
                    def command = isUnix() ? 'docker-compose build' : 'cmd /c "docker-compose build"'
                    sh command
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    def command = isUnix() ? 'docker-compose up -d' : 'cmd /c "docker-compose up -d"'
                    sh command
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def command = isUnix() ? 'docker-compose down && docker-compose up -d' : 'cmd /c "docker-compose down && docker-compose up -d"'
                    sh command
                }
            }
        }
    }
}
