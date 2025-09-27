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
                          ssh -i $SSH_KEY -o StrictHostKeyChecking=no ubuntu@3.91.27.71 "hostname -i"
                          scp -i $SSH_KEY -o StrictHostKeyChecking=no index.html ubuntu@3.91.27.71:/usr/share/ngnix/html

                        '''
                }
                echo 'Connecting to the Web Server...'
            }
        }
    }
}
