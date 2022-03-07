pipeline {
    agent any
    // parameters {
    //     string (name: 'GIT_URL', description: 'Enter git url')
    // }
    tools {
        maven 'maven-3.8'
    }
    stages {
        stage ('Code Checkout'){
            steps {
                git 'https://github.com/Guruprasanna30/javaapp.git'
            }
        }
        stage ('Build with Maven') {
            when {
                branch 'test'
            }
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('Code quality check with Sonarqube') {
             when {
                branch 'test'
            }
            steps {
                withSonarQubeEnv('sonarqube-8.9.7') {
                    sh "mvn sonar:sonar"
                }
            }
        }
    }
}