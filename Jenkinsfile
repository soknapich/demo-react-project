pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:21-alpine'
                    
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm install
                    npm run build

                '''
            }
        }
    }
}
