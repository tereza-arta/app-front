pipeline {
  agent any

  stages {
    stage('Build and Push Image') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'parandzem', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
          script {
            def myimage = docker.build("front")
            docker.withRegistry('https://hub.docker.com/', 'parandzem') {
              myimage.push()
            }
          }
        }
      }
    }
  }
}
