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
                // Add your web server connection steps here
                echo 'Connecting to the Web Server...'
            }
        }
    }
}
