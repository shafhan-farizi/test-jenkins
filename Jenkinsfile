pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Your build commands here
            }
        }
        stage('Test and Deploy') {
            parallel {
                stage('Test on Linux') {
                    agent {
                        label 'linux'
                    }
                    steps {
                        echo 'Running tests on Linux...'
                        // Your Linux test commands here
                    }
                }
                stage('Test on macOS') {
                    agent {
                        label 'macos'
                    }
                    steps {
                        echo 'Running tests on macOS...'
                        // Your macOS test commands here
                    }
                }
                stage('Deploy Dev') {
                    // This can run on the main agent if configured
                    steps {
                        echo 'Deploying to development environment...'
                    }
                }
            }
        }
    }
}
