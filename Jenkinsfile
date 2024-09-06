pipeline {
    agent any
    environment {
        EMAIL_RECIPIENT = 'missoceanocean18@gmail.com'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                echo 'Using Maven for build automation'
                bat 'echo "Build process completed."'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'Using JUnit for unit testing and Selenium for integration tests'
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
        stage('Code Analysis') {
            steps {
                echo 'Running code analysis...'
                echo 'Using SonarQube for static code analysis'
                bat 'echo "Code analysis completed."'
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins: Code Analysis Completed",
                        body: "The Code Analysis stage has completed successfully.\n\nCheck the attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                echo 'Using OWASP Dependency-Check for security vulnerabilities'
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
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                echo 'Simulating deployment using AWS CLI or Docker'
                bat 'echo "Deployment to staging completed."'
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins: Deploy to Staging Completed",
                        body: "The Deployment to Staging stage has completed successfully.\n\nCheck the attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                echo 'Using Selenium for integration tests on staging environment'
                bat 'echo "Integration tests on staging completed."'
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins: Integration Tests on Staging Completed",
                        body: "The Integration Tests on Staging stage has completed successfully.\n\nCheck the attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                echo 'Simulating deployment using AWS CLI or Docker'
                bat 'echo "Deployment to production completed."'
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins: Deploy to Production Completed",
                        body: "The Deployment to Production stage has completed successfully.\n\nCheck the attached logs for details.",
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
