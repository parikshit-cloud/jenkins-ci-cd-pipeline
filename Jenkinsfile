pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                url: 'https://github.com/parikshit-cloud/jenkins-ci-cd-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f demo-container || true
                docker run -d -p 8081:80 --name demo-container jenkins-demo-app
                '''
            }
        }
    }
}
