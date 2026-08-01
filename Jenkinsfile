pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install --upgrade pip'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                sh './venv/bin/pylint --disable=R,C hello.py'
            }
        }

        stage('Test') {
            steps {
                sh './venv/bin/python -m pytest -vv --cov=hello test_hello.py'
            }
        }
    }
}
