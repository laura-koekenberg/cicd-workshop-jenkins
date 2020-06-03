pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    sh './gradlew clean build -x test --no-daemon'// script om te builden
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh './gradlew test --no-daemon' // script om te testen
                }
            }
        }
        stage('Static code analysis') {
            steps {
                script {
                    sh './gradlew checkstyleMain --no-daemon' //run a gradle task// script om de code qualiteit te checken
                }
            }
        }
        stage('Deploy') {
            environment {
                HEROKU_API_KEY = credentials('secret-laura-heroku')
            }
            steps {
                script {
                    sh './gradlew deployHeroku --no-daemon' //run a gradle task
                }
            }
        }
    }
}
