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
        stage('test'){
            sh '''
                test -f build/index.html 
            '''
        }
    }
}
