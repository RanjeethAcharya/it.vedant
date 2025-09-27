pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
                sh 'pwd'
                sh 'ls -lrt'
            }
        }
        stage('Connecting to Web Server') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'server', keyFileVariable: 'SSH_KEY')]) {
                    sh '''
                      //scp -i "${SSH_KEY}" index.html ubuntu@3.91.27.71:/usr/share/nginx/html/index.html
                      ssh -i "${SSH_KEY}" -o StrictHostKeyChecking=no ubuntu@3.91.27.71 "sudo systemctl restart nginx.service"
                    '''
                }
            }
        }
    }
}
