pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World New'
            }
        }

        stage('build') {
            agent {
                docker {
                image 'node:18-alpine'
                reuseNode true
                }
            }
            steps {
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npn run build
                ls -la'''
            }
        }
    }
}
