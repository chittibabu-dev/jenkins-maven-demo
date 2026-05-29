pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '''
                echo "===== MAVEN BUILD ====="

                mvn clean package
                '''
            }
        }

        stage('Verify Artifact') {
            steps {
                sh '''
                echo "===== TARGET FOLDER ====="

                ls -la target
                '''
            }
        }
    }

    post {

        success {
            archiveArtifacts artifacts: 'target/*'
        }
    }
}
