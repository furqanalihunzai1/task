pipeline {
    agent any
 
    stages {
         
        stage('Build') {
            steps {
                
                
                // Build the Dockerfile
                
                sh 'docker build --tag=beyghakymyar/backend:1.0.$BUILD_NUMBER .'
            }
        }
        
        stage('Tag') {
            steps {
                // Tag latest image
                
                sh 'docker tag beyghakymyar/backend:1.0.$BUILD_NUMBER beyghakymyar/backend:1.0.$BUILD_NUMBER'
                
                // Tag Image with "latest"
                
                sh 'docker tag beyghakymyar/backend:1.0.$BUILD_NUMBER beyghakymyar/backend:$GIT_COMMIT'
            }
        }
        
        stage('Push') {
            steps {
                sh'docker login -u beyghakymyar -p yaaraan@123'
                // Push Image to DockerHub
               
                //sh 'docker push beyghakymyar/backend:$BUILD_NUMBER'
                
                // Push Tag to DockerHub
                
                sh 'docker push beyghakymyar/backend:1.0.$BUILD_NUMBER'
            }
        }
        
    }
}