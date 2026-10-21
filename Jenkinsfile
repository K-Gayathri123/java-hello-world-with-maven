
pipeline {
    agent any

    tools {
        jdk 'java'
        maven 'maven'
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
                echo 'Workspace cleaned'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Tools') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        always {
            junit testResults: '**/target/surefire-reports/TEST-*.xml',
                  allowEmptyResults: true
        }

        success {
            archiveArtifacts artifacts: '**/target/*.jar',
                             fingerprint: true
            echo 'Build successful!'
        }

        failure {
            echo 'Build failed. Check Console Output.'
        }
    }
}
