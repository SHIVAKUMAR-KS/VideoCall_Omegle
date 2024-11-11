pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/SHIVAKUMAR-KS/VideoCall_Omegle.git'
            }
        }
        stage('Build Docker Images') {
            steps {
                script {
                    sh 'docker-compose -f docker-compose.yml build'
                }
            }
        }
        stage('Run Containers') {
            steps {
                script {
                    sh 'docker-compose -f docker-compose.yml up -d'
                }
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
            sh 'docker-compose -f docker-compose.yml down'
        }
    }
}
