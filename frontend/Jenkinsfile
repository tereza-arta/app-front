pipeline {
  agent any
  stages {
    stage('Build and Push Inage') {
      steps {
        scropt {
          docker.withRegistry('https://index.docker.io/v1/', 'token for jenkins') {
            docker.build("terezabisharyan/front-repo")
            docker.image("terezabisharyan/front-repo").push()
          }
        }
      }
    }
  }
}
