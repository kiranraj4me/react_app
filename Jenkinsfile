pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git branch: 'main', changelog: false, credentialsId: '47924703-10e2-466d-96b2-15fa37b1bb72', poll: false, url: 'https://github.com/kiranraj4me/react_app'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
