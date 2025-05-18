pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Backend Image') {
            steps {
                dir('backend') {
                    sh 'docker build -t spotify-backend .'
                }
            }
        }
        stage('Build Frontend Image') {
            steps {
                dir('frontend') {
                    sh 'docker build -t spotify-frontend .'
                }
            }
        }
        stage('Start Services') {
            steps {
                sh 'docker-compose up -d --build'
            }
        }
    }
    post {
        always {
            echo 'Pipeline done!'
        }
    }
}
