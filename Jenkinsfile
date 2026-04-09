pipeline {
    agent any
    tools {
        gradle 'Gradle'
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
                sh 'mvn clean install'  // Maven build → JAR goes to target/
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'  // Maven test
            }
        }
        stage('Migrate Maven to Gradle') {
            steps {
                sh 'gradle init --type pom'  // Migrate to Gradle
            }
        }
        stage('Run Application') {
            steps {
                sh 'java -jar target/MyMavenToGradle-1.0-SNAPSHOT.jar'  // Run Maven-built JAR
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
