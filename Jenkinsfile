pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                cleanWs()
                bat 'git clone -b main https://github.com/MansiBurud/student-enroll.git'
            }
        }

        stage('Check Python') {
            steps {
                bat 'python --version'
                bat 'python -m pip --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('student-enroll') {
                    bat 'python -m pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('student-enroll') {
                    bat 'python -m pytest'
                }
            }
        }

        stage('Build App') {
            steps {
                dir('student-enroll') {
                    bat 'python setup.py install'
                }
            }
        }

        stage('Run App') {
            steps {
                dir('student-enroll') {
                    bat 'python app.py'
                }
            }
        }
    }

    post {
        failure {
            echo '🚫 Pipeline failed.'
        }
        success {
            echo '✅ Pipeline completed successfully.'
        }
    }
}
