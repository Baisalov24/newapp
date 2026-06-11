pipeline {
    agent any
    stages {
        stage ("clone") {
            steps {
                git url: "https://github.com/Baisalov24/newapp.git", branch: "main"
            }
        }
        stage("Build image") {
            steps {
                sh 'docker build -t timabai/test-app-image .'
            } 
        }
        stage("push") {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-creds',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {
                    sh '''
                    echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                    docker push timabai/test-app-image:latest
                    '''
                }
            }
        }
    }
}