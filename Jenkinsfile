pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    environment {
        SONARQUBE = 'My SonarQube Server'
    }

    stages {
        stage('Clone Repository') {
            steps {
                bat 'git clone https://github.com/syedmizba/jen-sonar.git'
                dir('jen-sonar') {
                    bat 'dir'
                }
            }
        }

        stage('Build') {
            steps {
                dir('jen-sonar') {
                    bat 'mvn clean install'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                dir('jen-sonar') {
                    withSonarQubeEnv("${SONARQUBE}") {
                        bat 'mvn sonar:sonar'
                    }
                }
            }
        }
    }
}
