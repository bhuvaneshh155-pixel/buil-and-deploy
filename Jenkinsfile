pipeline {
    agent any

    environment {
        APP_NAME    = 'MyPythonApp'
        APP_VERSION = '1.0.0'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                
                bat 'echo print("Application running successfully!") > app.py'
                
        
                bat 'python -m py_compile app.py'
            }
        }

        stage('Deploy') {
            steps {
                
                input message: "Approve deployment of ${env.APP_NAME} version ${env.APP_VERSION}?", 
                      ok: "Release"

                
                bat 'python app.py'
            }
        }
    }
}
