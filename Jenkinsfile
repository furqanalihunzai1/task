pipeline {
    agent {
        any {
            image 'docker:stable-dind'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Build and Push Docker Image') {
            steps {
                sh 'apt-get update && apt-get install -y docker-compose'
                sh 'docker login -u beyghakymyar -p yaaraan@123'
                sh 'docker-compose build'
                sh 'docker-compose push'
            }
        }
    }
}
