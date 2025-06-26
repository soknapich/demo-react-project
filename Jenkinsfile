pipeline {
    agent any
    // agent {
    //     docker {
    //         image 'node:21-alpine'
    //         //args '-u root' // run as root to install packages
    //     }
    // }

    stages {
        // stage('Build') {
        //      steps {
        //         sh '''
        //             npm install
        //             npm run build
        //         '''
        //     }
        // }

        // stage('Test') {
        //     steps {
        //         sh 'npm test'
        //     }
        // }

        stage('Install nginx Image') {
            steps {

                    sh 'pwd' // check workspace path
                    sh 'ls -l build' // make sure it exists
                    sh 'chmod -R 755 $WORKSPACE/build'
                    sh '''
                        docker stop node-nginx || true
                        docker rm node-nginx || true
                        docker run -d -p 8081:80 \
                        -v $WORKSPACE/build:/usr/share/nginx/html \
                        --name node-nginx \
                        nginx

                        docker cp $WORKSPACE/build/. node-nginx:/usr/share/nginx/html
                    '''

                // sh '''
                //     docker run -d -p 8081:80 -v $(pwd)/build:/usr/share/nginx/html nginx
                // '''
            }
        }


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
