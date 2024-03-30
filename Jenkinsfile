pipeline {
    agent any

    stages {
        stage('Cloning from git') {
            steps {
               git branch: 'master', url: 'https://github.com/Afraz33/MLCDPipeline'
            }
        }
                

       
        stage('Build and Push Docker Image') {
            steps {
                script {
                    
                    withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        
                        sh "docker build -t ${DOCKER_USERNAME}/mlops-ci/cd:latest ."

                        
                        sh "echo \"${DOCKER_PASSWORD}\" | docker login -u \"${DOCKER_USERNAME}\" --password-stdin"

                        
                        sh "docker push ${DOCKER_USERNAME}/mlops-ci/cd:latest"
                    }
                }
            }
        }
        stage('Email Notification') {
            steps {
                
                emailext subject: 'Jenkins Job Execution Successful',
                    body: 'The Jenkins job to containerize and push the application to Docker Hub was executed successfully.',
                    to: 'afraz3301@gmail.com'
            }
        }

    }
}
