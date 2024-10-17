pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh 'ls -l /home/automation/workspace/S7STUDENTS/s6kinga/kinga-do-it-yourself-checkout@2'
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
                // Check if the directory exists in the container
                sh 'ls -l /home/automation/workspace/S7STUDENTS/s6kinga/kinga-do-it-yourself-checkout@2'

                sh '''
                    if [ -f "package.json" ]; then
                        npm install
                        npm test --passWithNoTests
                    else
                        echo "package.json not found"
                        exit 1
                    fi
                '''
            }
        }
    }
}

