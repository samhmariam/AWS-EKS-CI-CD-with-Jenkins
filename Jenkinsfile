pipeline {
    envinronment {
        registry = "samhmariam/dockerproj"
        registryCredential = "docker-hub-id"
        dockerimage = ''
    }
    agent any
    stages {
        stage('Build Image') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('', registryCredential) {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}