pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Spring Boot jar'
                sh 'chmod +x mvnw || true'
                sh './mvnw clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                sh './mvnw test'
            }
        }

        stage('Archive') {
            steps {
                echo 'Saving jar artifact'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
