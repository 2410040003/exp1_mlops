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
                // Use Windows backslashes and the 'Scripts' directory
                bat '.\\venv\\Scripts\\python -m pip install --upgrade pip'
                bat '.\\venv\\Scripts\\pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                // Call pylint directly from the Windows Scripts folder
                bat '.\\venv\\Scripts\\pylint --disable=R,C hello.py'
            }
        }

        stage('Test') {
            steps {
                // Run pytest using the virtual environment's python executable
                bat '.\\venv\\Scripts\\python -m pytest -vv --cov=hello test_hello.py'
            }
        }
    }
}
