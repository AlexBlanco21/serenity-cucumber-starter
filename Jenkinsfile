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

    post {
        always {
            // This block will always run after the stages
            echo 'Post build steps - Always runs'

            // Send an email notification
            emailext(
                subject: "Build ${currentBuild.fullDisplayName}",
                body: "Build ${currentBuild.fullDisplayName} completed with status: ${currentBuild.currentResult}",
                to: 'ablancotamara@gmail.com'
            )
        }
        success {
            // This block runs only if the build is successful
            echo 'Build succeeded!'
            cucumber 'target/cucumber.json'
        }
        failure {
            // This block runs only if the build fails
            echo 'Build failed!'
        }
    }
}