pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t node-ci-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop node-app || exit 0'
                bat 'docker rm node-app || exit 0'
            }
        }

        stage('Run New Container') {
            steps {
                bat 'docker run -d -p 3000:3000 --name node-app node-ci-demo'
            }
        }
    }
}