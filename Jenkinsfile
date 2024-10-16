pipeline {
    agent any

    stages {
        stage('test') {
            agent {
                docker {
                    image 'node:22.4'
                    args '-u root'
                }
            }
            steps {
                sh '''
                    cd checkout
                    npm install
                    npm test --passWithNoTests
                '''
            }
        }
    }
}

