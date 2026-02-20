pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/samp80310/devops-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('devops-demo-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop existing container if running
                    sh 'docker rm -f devops-demo || true'
                    docker.image('devops-demo-app').run('-p 3000:3000 --name devops-demo')
                }
            }
        }
    }
}