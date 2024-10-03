pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the source code from GitHub
                git branch: 'master', url: 'https://github.com/AlexBlanco21/serenity-cucumber-starter.git'
            }
        }
        stage('Set up JDK') {
            steps {
                // Use JDK 17
                tool name: 'JDK 17', type: 'jdk'
            }
        }
        stage('Build') {
            steps {
                // Build the project with Maven
                sh 'mvn -B verify --file pom.xml'
            }
        }
    }
}
