pipeline {
    agent any
    parameters {
        string(
            name: 'BRANCH',
            defaultValue: 'main'
        )
        string(
            name: 'VERSION',
            defaultValue: '1.0'
        )
    }
    environment {
        APP_NAME = "demoapp"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: "${params.BRANCH}",
                url: 'https://github.com/Sathvik33/mvn-demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('Unit Testing') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Code Quality') {
            steps {
                echo "Quality Check"
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
}