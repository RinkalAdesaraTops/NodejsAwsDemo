pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/RinkalAdesaraTops/NodejsAwsDemo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker stop node-container || true
                    docker rm node-container || true
                    docker run -d -p 3000:3000 --name node-container nodejs-app
                '''
            }
        }
    }
}
