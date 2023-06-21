pipeline {
    agent any
    tools {
        git 'Default'
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: 'S'))
    }
    environment {
        DOCKERHUB_CREDENTIAL = credentials('Dock')
    }
    stages {
        stage('build') {
            steps {
                sh 'sudo docker build -t varugbhat/myapprepo1:myApp'
            }
        }
        stage('Push') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
                sh 'docker push varugbhat/myapprepo1:myApp'
            }
        }
    }
}
