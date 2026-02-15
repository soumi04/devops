pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/VARSHINI1805/jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t web134 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop web134 || true'
                sh 'docker rm web134 || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:80 --name web134 web134'
            }
        }
    }
}
