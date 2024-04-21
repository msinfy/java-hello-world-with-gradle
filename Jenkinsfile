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
                // Specify the SonarQube installation name
                script {
                    def scannerHome = tool 'SonarQube'; // Assuming 'SonarQube' is the installation name
                    withSonarQubeEnv('SonarQube') {
                        bat "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
