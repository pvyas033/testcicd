pipeline {
    agent any

    triggers {
        githubPullRequest()  // Ensure this trigger is set up in Jenkins
    }

    tools {
        nodejs 'NodeJS_18'
    }

    environment {
        NODE_ENV = 'test'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            junit 'test-results/*.xml'
        }
    }
}
