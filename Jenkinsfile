pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build Docker Image') {
      steps { sh 'docker build -t nginx-app:latest .' }
    }
    stage('Deploy Container') {
      steps {
        sh 'docker rm -f nginx-app || true'
        sh 'docker run -d --name nginx-app -p 80:80 nginx-app:latest'
      }
    }
  }
}
