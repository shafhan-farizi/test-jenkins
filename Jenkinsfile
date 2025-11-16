pipeline {
    agent any

    environment {
        IMAGE_NAME = 'shafhan/coba-bnsp'
        IMAGE_TAG = 'latest'
        DOCKER_CREDENTIALS = 'docker-id'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Memulai proses checkout'
                echo 'Kode diambil dari GitHub: ${GIT_URL} Branch: ${BRANCH_NAME}'
            }
        }

        stage('Build') {
            steps {
                echo 'Memulai proses build'

                script {
                    withCredentials([usernamePassword(
                        credentialsId: ${DOCKER_CREDENTIALS},
                        usernameVariable: 'DOCKER_USR',
                        passwordVariable: 'DOCKER_PWD'
                    )]) {
                        echo 'Membangun image'
                        sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG}'

                        sh '''

                            echo 'Login Docker'
                            echo ${DOCKER_PWD} | docker login -u ${DOCKER_USR} --password-stdin
                            
                            echo 'Push image ke docker hub'
                            docker push ${IMAGE_NAME}:${IMAGE_TAG}

                            echo 'Logout Docker
                            docker logout
                        '''
                    }
                }
            }
        }

    }
}