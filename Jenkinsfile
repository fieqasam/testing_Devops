pipeline {
    agent any
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                apt update
                apt upgrade -y
                apt-get install python3 -y
                apt-get install python3-venv-y
		apt-get install python3-pip-y
		python3 -m venv env
		. env/bin/activate
		python3 -m pip install DateTime
            }
        }
        stage('Test') {
            steps {
                sh '''
                python3 -V
                '''
            }
        }
        stage('Deliver') {
            steps {
                sh '''
                . env/bin/activate
		python3 py_test.py
                '''
            }
        }
    }
}
