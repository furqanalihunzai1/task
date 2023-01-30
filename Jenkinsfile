pipeline {
    agent any
 
    stages {
         stage('Clone') {
            steps {
                git 'https://github.com/HakeemYB/task.git'
            }
        }
        stage('Build') {
            steps {
                
                
                // Build the Dockerfile
                sh 'docker build --tag=beyghakymyar/frontend:$BUILD_NUMBER /my-app/Dockerfile'
                sh 'docker build --tag=beyghakymyar/backend:$BUILD_NUMBER .'
            }
        }
        
        stage('Tag') {
            steps {
                // Tag latest image
                sh 'docker tag beyghakymyar/frontend:$BUILD_NUMBER beyghakymyar/frontend:latest'
                sh 'docker tag beyghakymyar/backend:$BUILD_NUMBER beyghakymyar/backend:latest'
                
                // Tag Image with "latest"
                sh 'docker tag beyghakymyar/frontend:$BUILD_NUMBER beyghakymyar/frontend:$GIT_COMMIT'
                sh 'docker tag beyghakymyar/backend:$BUILD_NUMBER beyghakymyar/backend:$GIT_COMMIT'
            }
        }
        
        stage('Push') {
            steps {
                sh'docker login -u beyghakymyar -p yaaraan@123'
                // Push Image to DockerHub
                sh 'docker push beyghakymyar/frontend:$BUILD_NUMBER'
                sh 'docker push beyghakymyar/backend:$BUILD_NUMBER'
                
                // Push Tag to DockerHub
                sh 'docker push beyghakymyar/frontend:latest'
                sh 'docker push beyghakymyar/backend:latest'
            }
        }
        
    }
}