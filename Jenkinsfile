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


        stage('Install and Run Nginx') {
            steps {
                script {
                    // Assuming Jenkins agent is Linux with apt-get
                    sh '''
                        apt-get update
                        apt-get install -y nginx
                    '''
                    // Copy built files to Nginx root (adjust paths)
                    sh '''
                        rm -rf /var/www/html/*
                        cp -r build/* /var/www/html/
                        systemctl restart nginx
                    '''
                }
            }
        }


    }
}
