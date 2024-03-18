pipeline {
  agent any
  stages {
    stage('Build and Push Inage') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'docker-pat') {
            docker.build("terezabisharyan/front-repo")
            docker.image("terezabisharyan/front-repo").push()
          }
        }
      }
    }
  }
}
