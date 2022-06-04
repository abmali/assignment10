pipeline {
  environment {
    registry = "dockerabhijeet/hello-docker-java"
    registryCredential = 'doc1'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
