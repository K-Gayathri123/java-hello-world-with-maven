
pipeline {
    agent any
    stages {
        stage('Clean Workspace')
        {
            steps {
                cleanWs()
                echo 'Workspace cleaned successfully'
            }
        }

        stage('Checkout') 
        {
            steps {
                git branch: 'master',
                    url: 'https://github.com/K-Gayathri123/java-hello-world-with-maven.git'
            }
        }

        stage('Check Java and Maven')
        {
            steps {
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Clean Build') 
        {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Compile')
        {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') 
        {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package')
        {
            steps {
                sh 'mvn package'
            }
        }
    }

}
