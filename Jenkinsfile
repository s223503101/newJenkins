pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'oceanthakral@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Using a simple echo command instead of a shell command
                // to simulate the build process on Windows
                bat 'echo "Build process completed."'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Simulate a test process
                bat 'echo "Tests completed."'
            }
            post {
                always {
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Unit and Integration Tests Completed",
                        body: "The Unit and Integration Tests stage has completed successfully.",
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                // Simulate a security scan process
                bat 'echo "Security scan completed."'
            }
            post {
                always {
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Security Scan Completed",
                        body: "The Security Scan stage has completed successfully.",
                        attachLog: true
                    )
                }
            }
        }
    }

    post {
        success {
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Jenkins Pipeline: Build Success",
                body: "The Jenkins pipeline completed successfully and the application has been built and tested.",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Jenkins Pipeline: Build Failed",
                body: "The Jenkins pipeline failed. Please check the Jenkins logs for more details.",
                attachLog: true
            )
        }
    }
}
