pipeline {
    agent any
    stages {
        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }
        stage('Clone Project') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat './gradlew.bat clean build'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Ensure that SonarQube environment is properly configured
                withSonarQubeEnv() {
                    // Run SonarQube analysis task
                    bat "./gradlew sonar"
                }
            }
        }
    }
}
