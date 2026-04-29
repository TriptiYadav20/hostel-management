pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/TriptiYadav20/hostel-management.git'
            }
        }
        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t hostel-management .'
            }
        }
        stage('Run Container (Test)') {
            steps {
                bat 'docker stop hostel-test || true'
                bat 'docker rm hostel-test || true'
                bat 'docker run -d --name hostel-test -p 8080:8080 hostel-management'
            }
        }
    }
}