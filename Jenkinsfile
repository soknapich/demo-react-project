pipeline {
    agent {
        docker {
            image 'node:21-alpine'
        }
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm install

                '''
            }
        }
        stage('Build') {
             steps {
                sh '''
                    npm run build
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
