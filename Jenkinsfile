pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from your SCM (e.g., Git)
                checkout scm
            }
        }

        stage('test') {
            agent {
                docker {
                    image 'node:22.4'
                    args '-u root'
                }
            }
            steps {
                // Ensure we're in the correct directory
                sh '''
                    if [ -d "checkout" ]; then
                        cd checkout
                    fi
                    npm install
                    npm test --passWithNoTests
                '''
            }
        }
    }
}

