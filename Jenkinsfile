pipeline {
  environment {
    registry = "samhmariam/capstone"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Lint') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Building Image') {
      steps{
        script {
          dockerImage = docker.build registry + ":v1"
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
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:v1"
      }
    }
  }
}