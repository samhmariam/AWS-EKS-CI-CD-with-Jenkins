pipeline {
    agent any
    stages {
        stage('Build Image') {
            steps {
                app = docker.build(samhmariam/dockerproj)
            }
        }
        stage('Push Image') {
            steps {
                docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-id') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                }
            }
        }
    }
}