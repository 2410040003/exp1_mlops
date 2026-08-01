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
                bat 'python -m venv venv'
                bat './venv/bin/pip install --upgrade pip'
                bat './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                bat './venv/bin/pylint --disable=R,C hello.py'
            }
        }

        stage('Test') {
            steps {
                bat './venv/bin/python -m pytest -vv --cov=hello test_hello.py'
            }
        }
    }
}
