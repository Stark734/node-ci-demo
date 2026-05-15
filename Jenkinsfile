pipeline {
    agent any

    stages {

        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-ci-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop node-app || true'
                sh 'docker rm node-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name node-app node-ci-demo'
            }
        }
    }
}