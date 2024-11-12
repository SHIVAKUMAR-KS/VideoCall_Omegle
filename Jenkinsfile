pipeline {
    agent any
    
    environment {
        DOCKER_COMPOSE_PATH = 'docker-compose.yml'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/SHIVAKUMAR-KS/VideoCall_Omegle.git'
            }
        }
        stage('Build Docker Images') {
            steps {
                script {
                    sh "docker-compose -f ${DOCKER_COMPOSE_PATH} build"
                }
            }
        }
        stage('Run Containers') {
            steps {
                script {
                    sh "docker-compose -f ${DOCKER_COMPOSE_PATH} up -d"
                }
            }
        }
    }
    
    post {
        always {
            echo 'Cleaning up Docker containers...'
            sh "docker-compose -f ${DOCKER_COMPOSE_PATH} down"
        }
    }
}
