pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'oceanthakral@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Build step
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Test steps
            }
            post {
                always {
                    // Send email notification after this stage
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Unit and Integration Tests Stage - ${currentBuild.currentResult}",
                        body: "The Unit and Integration Tests stage completed with status: ${currentBuild.currentResult}",
                        attachLog: true
                    )
                }
            }
        }

        // Other stages...

        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                // Security scan steps
            }
            post {
                always {
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Security Scan Stage - ${currentBuild.currentResult}",
                        body: "The Security Scan stage completed with status: ${currentBuild.currentResult}",
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
                body: "The Jenkins pipeline completed successfully. The application has been deployed to production.",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Jenkins Pipeline: Build Failed",
                body: "The Jenkins pipeline failed. Please check the attached logs for more details.",
                attachLog: true
            )
        }
    }
}
