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
                    sh 'npm install'
                }
            }
        }

        stage('Start Application') {
            steps {
                script {
                    echo 'Starting the application...'
                    sh 'npm start & sleep 5' // Ensures the app has time to start before proceeding
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    echo 'Running Mocha tests...'
                    sh 'npm run start-tests'
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
