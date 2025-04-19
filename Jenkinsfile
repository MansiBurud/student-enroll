pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from Git repository, specify the correct branch name (main)
                bat 'git clone -b main https://github.com/MansiBurud/student-enroll.git'
            }
        }

        // stage('Install Dependencies') {
        //     steps {
        //         // Install dependencies from the requirements.txt file
        //         bat 'pip install -r requirements.txt'
        //     }
        // }

        stage('Run Tests') {
            steps {
                // Add your test running command here
                bat 'pytest'  // For example, if you're using pytest for testing
            }
        }

        stage('Build App') {
            steps {
                // Add your build steps here
                bat 'python setup.py install'  // Example build command
            }
        }

        stage('Run App') {
            steps {
                // Run the application
                bat 'python app.py'  // Example command to run the app
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed.'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
    }
}
