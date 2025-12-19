pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/mikailm2i/my-python.git'
            }
        }

        stage('Run tests') {
            steps {
                sh 'python3 -m unittest discover'
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t my-python-app .'
            }
        }

        stage('Run Docker container') {
            steps {
                sh '''
                docker rm -f my-python-container || true
                docker run -d --name my-python-container my-python-app
                '''
            }
        }
    }
}

