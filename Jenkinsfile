pipeline {
    agent any
    environment {
        EMAIL_RECIPIENT = 'missoceanocean18@gmail.com'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                bat 'echo "Build process completed."'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                bat 'echo "Tests completed."'
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins: Unit and Integration Tests Completed",
                        body: "The Unit and Integration Tests stage has completed successfully.\n\nCheck the attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                bat 'echo "Security scan completed."'
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins: Security Scan Completed",
                        body: "The Security Scan stage has completed successfully.\n\nCheck the attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
    }
    post {
        success {
            emailext(
                subject: "Jenkins Pipeline: Build Success",
                body: "The Jenkins pipeline completed successfully and the application has been built and tested.\n\nCheck the attached logs for details.",
                to: "${EMAIL_RECIPIENT}",
                attachLog: true
            )
        }
        failure {
            emailext(
                subject: "Jenkins Pipeline: Build Failed",
                body: "The Jenkins pipeline failed. Please check the Jenkins logs for more details.",
                to: "${EMAIL_RECIPIENT}",
                attachLog: true
            )
        }
    }
}
