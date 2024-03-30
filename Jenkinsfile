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
                    // Load environment variables from file
                    def dockerEnv = readProperties file: 'docker.env'

                    // Build Docker image
                    sh "docker build -t ${dockerEnv.DOCKER_USERNAME}/your-image-name:latest ."

                    // Authenticate with Docker Hub
                    sh "echo \"${dockerEnv.DOCKER_PASSWORD}\" | docker login -u \"${dockerEnv.DOCKER_USERNAME}\" --password-stdin"

                    // Push Docker image to Docker Hub
                    sh "docker push ${dockerEnv.DOCKER_USERNAME}/your-image-name:latest"
                }
            }
        }
    }
}
