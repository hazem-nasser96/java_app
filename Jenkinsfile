pipeline {
    agent any

    environment {
        MAVEN_CMD = './mvnw' // Maven wrapper command
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Set Up Maven Wrapper Permissions') {
            steps {
                echo 'Making Maven Wrapper executable...'
                sh 'chmod +x mvnw'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh "${MAVEN_CMD} clean install"
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh "${MAVEN_CMD} test"
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                sh "${MAVEN_CMD} package"
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }

        failure {
            echo 'Build failed. Please check the logs.'
        }
    }
}

