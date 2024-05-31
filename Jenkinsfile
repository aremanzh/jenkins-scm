pipeline {
    agent any
    triggers {
        pollSCM('*/5 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                apt update
                apt upgrade -y
                apt-get install python3 -y
                apt-get install python3-venv -y
                apt-get install python3-pip -y
                python3 -m venv .venv
                
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                . .venv/bin/activate
                pip install DateTime
                python3 -V
                python3 kualalumpur.py
                '''
            }
        }
        stage('Deliver') {
            steps {
                sh '''
                echo "Ready to deliver"
                '''
            }
        }
    }
}
