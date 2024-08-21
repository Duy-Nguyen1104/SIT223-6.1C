pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project using Maven'
                // Tool: Maven
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit'
                // Tools: JUnit
            }
            post {
                success {
                    mail to: 'duyng2311@gmail.com',
                    subject: 'Jenkins Test Notification',
                    body: 'All unit and integration tests passed',
                    attachLog: true
                }
                failure {
                    mail to: 'duyng2311@gmail.com',
                    subject: 'Jenkins Test Failure',
                    body: 'Some tests failed. Please check the Jenkins logs for details.',
                    attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube'
                // Tool: SonarQube
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with Snyk Code'
                // Tool: Snyk Code
            }
            post {
                success {
                    mail to: 'duyng2311@gmail.com',
                    subject: 'Jenkins Security Scan Notification',
                    body: 'Security scan completed successfully',
                    attachLog: true
                }
                failure {
                    mail to: 'duyng2311@gmail.com',
                    subject: 'Jenkins Security Scan Failure',
                    body: 'Security vulnerabilities detected. Please review the Jenkins logs for details.',
                    attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to AWS EC2 Staging'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging using Maven'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to AWS EC2 Production'
            }
        }
    }
}
