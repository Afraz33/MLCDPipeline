pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Execute shell command to echo a message along with branch name
                sh "echo 'Hello, this is a test job from Jenkins! Branch: ${env.BRANCH_NAME}'"
            }
        }
    }
}
