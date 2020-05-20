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
          dockerImage = docker.build registry + ":v2"
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
    stage('Deploy Container') {
      steps{
        kubernetesDeploy(
          kubeconfigId: 'kubeconfig',
          configs:  'deployment-blue.yml'
        )
      }
    }
  }
}