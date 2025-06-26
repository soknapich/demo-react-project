pipeline {
    agent any

    environment {
        NODE_IMAGE = 'node:21-alpine'
        BUILD_DIR = 'build'  // or 'dist' if using Vite
    }

    stages {
        stage('Install & Build') {
            agent {
                docker {
                    image "${NODE_IMAGE}"
                }
            }
            steps {
                sh '''
                    npm install
                    npm run build
                '''
            }
        }

        stage('Remove Nginx') {
            agent any  // run this on host where Docker CLI works
                steps {
                    sh '''
                        docker stop node-nginx || true
                        docker rm node-nginx || true
                    '''
                }
        }

        stage('Run NGINX') {
            agent any  // run this on host where Docker CLI works
            steps {
                sh '''
                    docker run -d --name node-nginx -p 8082:80 nginx
                '''
            }
        }

        stage('Copy build files') {
            agent any  // run this on host where Docker CLI works
            steps {
                sh '''
                    docker cp ${BUILD_DIR}/. node-nginx:/usr/share/nginx/html
                '''
            }
        }

    }
}

