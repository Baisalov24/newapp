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
                sh 'docker build -t test-image .'
            } 
        }
        stage("Run conatainer") {
            steps {
                sh 'docker run -d -p 80:80 --name headphone-container test-image'
            }
        }
    }
}