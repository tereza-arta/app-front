pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-credential')
  }
  stages {
    stage('SCM Checkout') {
      steps {
        git 'https://github.com/tereza-arta/three-tier-app.git'
      }
    }
    stage('Build docker image') {
      steps {
        sh 'docker build -t terezabisharyan/front:$BUILD_NUMBER .'
      }
    }
    stage('Login to dockerhub') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push image') {
      steps {
        sh 'docker push terezabisharyan/front:$BUILD_NUMBER'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
