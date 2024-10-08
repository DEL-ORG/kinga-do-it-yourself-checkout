pipeline {
    agent any

    stages {
        stage('Scan Golang Code') {
            agent {
                docker {
                    image 'golang:1.22.5'
                    args '-u root:root' // Run the container as root
                }
            }
            steps {
                sh '''
                    cd do-it-yourself/src/catalog/
                    go test
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    ls
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}

