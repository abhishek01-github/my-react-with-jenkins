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
                sh 'sleep 10'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install' // Install project dependencies
                sh 'sleep 10'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'npm test' // Run unit tests
                sh 'sleep 10'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build' // Build the React app
                sh 'sleep 10'
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
