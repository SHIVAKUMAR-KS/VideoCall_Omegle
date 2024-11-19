pipeline {
    agent any
    environment {
        DOCKER_COMPOSE = 'docker-compose'
    }
    stages {
        stage('Checkout') {
            steps {
                // Clone the Git repository
                git branch: 'main', url: 'https://github.com/SHIVAKUMAR-KS/VideoCall_Omegle.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Build the Docker images using docker-compose
                    sh '''
                        docker-compose -f docker-compose.yml build
                    '''
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Start the containers, run tests, then shut down
                    sh '''
                        docker-compose up -d
                        # Adjust for your testing setup, for example:
                        # docker exec -t <container_name> npm test
                        docker-compose down
                    '''
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy using docker-compose (bring up the containers)
                    sh '''
                        docker-compose up -d
                    '''
                }
            }
        }
    }
    post {
        always {
            // Clean up Docker containers after each run
            sh 'docker-compose down || true'
        }
    }
}
