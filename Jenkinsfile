pipeline {
    agent any

    stages {
        stage('Build') {
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
                    npm --version
                    npm ci --no-audit --no-fund --prefer-offline
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
