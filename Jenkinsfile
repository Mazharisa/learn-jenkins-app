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
                npm run build
                ls -la
                npm test
                '''
            }
        }

        stage('Test build2') {
            steps {
                sh '''
                echo Test build
                ls -l ./build
                '''
            }
        }
        
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
