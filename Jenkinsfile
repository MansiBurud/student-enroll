pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from Git repository, specify the correct branch name (main)
                git branch: 'main', url: 'https://github.com/MansiBurud/student-enroll.git'
            }
        }

        // stage('Install Dependencies') {
        //     steps {
        //         // Install dependencies from the requirements.txt file
        //         sh 'pip install -r requirements.txt'
        //     }
        // }

        stage('Run Tests') {
            steps {
                // Add your test running command here
                sh 'pytest'  // For example, if you're using pytest for testing
            }
        }

        stage('Build App') {
            steps {
                // Add your build steps here
                sh 'python setup.py install'  // Example build command
            }
        }

        stage('Run App') {
            steps {
                // Run the application
                sh 'python app.py'  // Example command to run the app
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
