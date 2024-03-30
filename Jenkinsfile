pipeline {
    agent any

    stages {
        stage('Cloning from git') {
            steps {
               git branch: 'master', url: 'https://github.com/Afraz33/MLCDPipeline'
            }
        }
        stage('Build') {
            steps {
                // Execute shell command to echo a message along with branch name
                env.BRANCH_NAME = scm.branches[0].name
                echo "Branch name: ${env.BRANCH_NAME}"
                sh "echo 'Hello, this is a test job from Jenkins! Branch: ${env.BRANCH_NAME}'"
            }
        }
    }
}
