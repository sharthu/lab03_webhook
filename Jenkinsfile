pipeline {
    agent {
        label 'aws-agent'
    }
    environment {
        workspace = "/home/ubuntu/project/testwebhook"
    }
    stages {
        stage('Checkout Source') {
            steps {
                ws("${workspace}") {
                    checkout scm
                }
            }
        }
        stage('Docker Compose Build') {
           steps {
                ws("${workspace}") {
                    sh "docker compose build --no-cache frontend backend"
                }
           }
        }
        stage('Docker Compose Up') {
            steps {
                ws("${workspace}") {
                    sh "docker compose up --no-deps -d frontend backend"
                }
            }
        }
    }
}