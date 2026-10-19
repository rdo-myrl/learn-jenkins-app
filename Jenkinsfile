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
            environment {
                npm_config_cache = "${WORKSPACE}/.npm"
            }
            steps {
                sh '''
                    rm -rf node_modules
                    node --version
                    npm --version
                    npm ci --no-audit --no-fund || { tail -n 80 .npm/_logs/*-debug-0.log; exit 1; }
                    npm run build
                '''
            }
        }
    }
}