pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'oceanthakral@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
            post {
                always {
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Unit and Integration Tests Completed",
                        body: "The Unit and Integration Tests stage has completed successfully."
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
            }
            post {
                always {
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Security Scan Completed",
                        body: "The Security Scan stage has completed successfully."
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
                body: "The Jenkins pipeline has completed successfully and the application has been deployed."
            )
        }
        failure {
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Jenkins Pipeline: Build Failed",
                body: "The Jenkins pipeline has failed. Please check the Jenkins logs for more details."
            )
        }
    }
}
