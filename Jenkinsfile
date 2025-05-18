pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Raunakmali08/Spotify-clone-.git'
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

        stage('Run Containers') {
            steps {
                sh 'docker run -d -p 5000:5000 --name backend spotify-backend'
                sh 'docker run -d -p 80:80 --name frontend spotify-frontend'
            }
        }
    }

    post {
        always {
            echo "Pipeline done!"
        }
    }
}

