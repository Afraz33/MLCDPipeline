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
                        
                        sh "docker build -t ${DOCKER_USERNAME}/MLOPS-CD/CD:latest ."

                        
                        sh "echo \"${DOCKER_PASSWORD}\" | docker login -u \"${DOCKER_USERNAME}\" --password-stdin"

                        // Push Docker image to Docker Hub
                        sh "docker push ${DOCKER_USERNAME}/MLOPS-CD/CD:latest"
                    }
                }
            }
        }
    }
}
