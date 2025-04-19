pipeline {
    agent any

    environment {
        PYTHON_ENV = 'python3'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the code from the repository
                git 'https://github.com/MansiBurud/student-enroll.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install the dependencies from the requirements.txt file
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Placeholder to run any tests (you can modify this if you add tests)
                sh 'pytest'
            }
        }

        stage('Build App') {
            steps {
                // Build your app if required (usually unnecessary for Streamlit apps)
                echo 'Building app...'
            }
        }

        stage('Run App') {
            steps {
                // Run the Streamlit app for CI purposes
                sh 'streamlit run app.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
