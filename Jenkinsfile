pipeline {
    agent any
    // agent {
    //     docker {
    //         image 'node:21-alpine'
    //         args '-u root' // run as root to install packages
    //     }
    // }

    stages {
        stage('Install Image') {
            steps {
                sh '''
                    docker run -d -p 8081:80 -v $(pwd):/usr/share/nginx/html:ro nginx
                '''
            }
        }
        // stage('Build') {
        //      steps {
        //         sh '''
        //             npm run build
        //         '''
        //     }
        // }

        // stage('Test') {
        //     steps {
        //         sh 'npm test'
        //     }
        // }


        // stage('Install and Run Nginx') {
        //     steps {
        //         script {
        //             // Assuming Jenkins agent is Linux with apt-get
        //             sh '''
        //                 apt-get update
        //                 apt-get install -y nginx
        //             '''
        //             // Copy built files to Nginx root (adjust paths)
        //             sh '''
        //                 rm -rf /var/www/html/*
        //                 cp -r build/* /var/www/html/
        //                 systemctl restart nginx
        //             '''
        //         }
        //     }
        // }


    }
}
