pipeline {
    agent any
    environment {
        EMAIL_RECIPIENT = 'missoceanocean18@gmail.com'
    }
    
    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
                echo 'Detail: Build code using automation tool which will compile and package'
                bat 'mvn clean install' // Simulating Maven build
            }
        }
        
        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Test'
                bat 'mvn test' // Simulating JUnit and Selenium tests
            }
            post {
                success {
                    emailext(
                        subject: "Jenkins: Unit and Integration Test Successful",
                        body: "Stage 2 successfully implemented. Please refer to the logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        subject: "Jenkins: Unit and Integration Test Failed",
                        body: "Stage 2 failed. Please check the attached logs for more details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        
        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
                bat 'sonar-scanner' // Simulating code analysis with SonarQube
            }
        }
        
        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
                bat 'dependency-check' // Simulating a security scan with OWASP Dependency-Check
            }
            post {
                success {
                    emailext(
                        subject: "Jenkins: Security Scan Successful",
                        body: "Stage 4 completed successfully. Please refer to the logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        subject: "Jenkins: Security Scan Failed",
                        body: "Stage 4 failed. Please check the attached logs for more details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        
        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
                bat 'aws deploy --application-name MyApp --deployment-group StagingGroup' // Simulating deployment to staging
            }
        }
        
        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
                bat 'selenium-tests' // Simulating integration tests on staging
            }
        }
        
        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
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


