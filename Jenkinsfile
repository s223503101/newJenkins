pipeline {
    agent any
    environment {
        EMAIL_RECIPIENT = 'missoceanocean18@gmail.com'
    }
    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                bat 'mvn clean install' // Simulating Maven build
            }
        }
        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit and integration tests with Selenium...'
                bat 'mvn test' // Simulating JUnit and Selenium tests
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
        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code using SonarQube...'
                bat 'sonar-scanner' // Simulating code analysis with SonarQube
            }
        }
        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency-Check...'
                bat 'dependency-check' // Simulating a security scan with OWASP Dependency-Check
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
        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server using AWS CLI...'
                bat 'aws deploy --application-name MyApp --deployment-group StagingGroup' // Simulating deployment to staging
            }
        }
        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment using Selenium...'
                bat 'selenium-tests' // Simulating integration tests on staging
            }
        }
        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server using AWS CLI...'
                bat 'aws deploy --application-name MyApp --deployment-group ProductionGroup' // Simulating deployment to production
            }
        }
    }
    post {
        success {
            emailext(
                subject: "Jenkins Pipeline: Build Success",
                body: "The Jenkins pipeline completed successfully and the application has been built, tested, and deployed.\n\nCheck the attached logs for details.",
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
