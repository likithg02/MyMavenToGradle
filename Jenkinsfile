pipeline {
    agent any  // Use any available agent
    tools {
        gradle 'Gradle'  // Ensure this matches the name configured in Jenkins
        jdk 'JDK'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/likithg02/MyMavenToGradle.git'
            }
        }
        stage('Build') {
            steps {
                sh 'gradle build'  // Run Gradle build
            }
        }
        stage('Test') {
            steps {
                sh 'gradle test'  // Run unit tests
            }
        }
        stage('Migrate Maven to Gradle') {
            steps {
                sh 'gradle init --type pom'  // Migrate Maven project to Gradle
            }
        }
        stage('Run Application') {
            steps {
                // Start the JAR application
                sh 'gradle run'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
