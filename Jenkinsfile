pipeline {
    agent any

    stages {
        stage('Build') {
            environment {
                DOCKER_CRED = credentials('docker-id')
            }

            steps {
                // sh 'docker login -u shafhan'
                echo 'awikwaokwaok'
                echo $DOCKER_CRED_USR
            }
        }

    }
}