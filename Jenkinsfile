pipeline {

agent { label 'all_agents' }


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
                //sh "./mvnw clean install"
                sh './mvnw clean install'
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

