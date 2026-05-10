pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Dhusinth/-project1-static-cicd.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t dhusinth123/mynginx:latest . || true'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: '01',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push dhusinth123/mynginx:latest'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker rm -f mynginx || true'
                sh 'docker run -d -p 80:80 --name mynginx dhusinth123/mynginx:latest'
            }
        }
    }
}
