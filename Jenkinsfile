pipeline {
    agent any

    stages {
        stage('build') {
            agent{
                docker{
                    image 'node:24-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    npm --version
                    node --version
                    npm ci
                    npm run build
                '''
            }
        }
        stage('Test'){
            steps{
            sh '''
                test -f build/index.html 
            '''
            }
        }
    }

    post{
        always{
            junit 'test-result/junit.xml'
        }
    }
}
