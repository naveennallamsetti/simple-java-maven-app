pipeline {
    agent any

    tools {
        maven 'maven3'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/naveennallamsetti/simple-java-maven-app.git'
            }
        }

        stage('validate') {
            steps {
                sh 'mvn validate'
            }
        }
        stage('compile stage') {
            steps {
                sh 'mvn compile'
            }
        }  
        stage('test stage') {
            steps {
                sh 'mvn test'
            }
        }
        stage('package stage') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-java-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8080:8080 simple-java-app'
            }
        }
    }
}
