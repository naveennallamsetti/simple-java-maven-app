pipeline {
    agent any

    tools {
        maven 'maven3'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'master',
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
        sh '''
        docker rm -f simple-java-app-container || true
        docker run -d --name simple-java-app-container simple-java-app
        '''
    }
}
    }
}
