pipeline {
    agent any

    environment {
        // Define environment variables here
        STAGING_SERVER = 'staging-server-address'
        PRODUCTION_SERVER = 'production-server-address'
        EMAIL_RECIPIENT = 'kirtikasharma5104@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Replace with the actual build command
                sh 'mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Replace with the actual test commands
                sh 'mvn test'
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
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                // Replace with the actual security scan command
                sh 'zap-baseline.py -t http://localhost:8080 -r zap_report.html'
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
                sh 'scp target/app.war user@${STAGING_SERVER}:/path/to/deploy/'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Replace with the actual staging tests command
                sh 'curl -X GET http://${STAGING_SERVER}/health-check'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Replace with the actual deployment command
                sh 'scp target/app.war user@${PRODUCTION_SERVER}:/path/to/deploy/'
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
