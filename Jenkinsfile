pipeline {
    agent any

    // environment {
    //     NODE_ENV = 'production'  // Set environment variable if needed
    // }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/yamachevaGreta/Student-Registry-App-Docker'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    echo 'Installing dependencies...'
                    bat 'npm install'
                }
            }
        }

        stage('Start Application') {
            steps {
                script {
                    echo 'Starting the application...'
                    bat 'start /B npm start' // Runs in the background
                    bat 'timeout /T 5'      // Waits 5 seconds before proceeding
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    echo 'Running Mocha tests...'
                    bat 'npm run start-tests'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
