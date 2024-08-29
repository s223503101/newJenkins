pipeline {
    agent any

    environment {
        // Define environment variables here
        STAGING_SERVER = 'staging-server-address'
        PRODUCTION_SERVER = 'production-server-address'
        EMAIL_RECIPIENT = 'oceanthakral@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Replace with the actual build command
                
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Replace with the actual test commands
                
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

        stage('Code Analysis') {
            steps {
                echo 'Running code analysis...'
                // Replace with the actual code analysis command
        
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                // Replace with the actual security scan command
                
            }
            post {
                always {
                    // Send email notification after this stage
                    emailext(
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Jenkins: Security Scan Stage - ${currentBuild.currentResult}",
                        body: "The Security Scan stage completed with status: ${currentBuild.currentResult}",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // Replace with the actual deployment command
                
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Replace with the actual staging tests command
                
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Replace with the actual deployment command
                
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
