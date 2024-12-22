pipeline {

agent { label 'agent1' }

    stages {
        

        

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

