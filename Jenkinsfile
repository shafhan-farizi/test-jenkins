pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    withCredentials([usernamePassword(
                        credentialsId: 'docker-id',
                        usernameVariable: 'DOCKER_USR',
                        passwordVariable: 'DOCKER_PWD'
                    )]) {
                        sh 'echo \$DOCKER_PWD | docker login -u \$DOCKER_USR --password-stdin'
                    }
                }
            }
        }

    }
}