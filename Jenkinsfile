pipeline {
    agent any
    tools {
        nodejs 'my-nodejs'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from the GitHub repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install' // Install project dependencies
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat 'npm test' // Run unit tests
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build' // Build the React app
            }
        }

        stage('Publish Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/build/**', allowEmptyArchive: true // Archive build artifacts
            }
        }
    }

    post {
        always {
            junit 'junit.xml' // Publish JUnit test reports
        }
    }
}
