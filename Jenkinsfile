pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project using Maven'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit'
            }
            post {
                success {
                    script {
                        archiveArtifacts artifacts: '**/*', excludes: ''
                        mail to: "duyng2311@gmail.com",
                             subject: "Jenkins Pipeline: Unit and Integration Tests Stage - ${currentBuild.currentResult}",
                             body: "The Unit and Integration Tests stage has completed with status: ${currentBuild.currentResult}.",
                             attachmentsPattern: '*/target/*.log'
                    }
                }
                failure {
                    script {
                        archiveArtifacts artifacts: '**/*', excludes: ''
                        mail to: "duyng2311@gmail.com",
                             subject: "Jenkins Pipeline: Unit and Integration Tests Stage - ${currentBuild.currentResult}",
                             body: "Unit and integration tests failed. ${currentBuild.currentResult}.",
                             attachmentsPattern: '**/target/*.log'
                    }
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube'
            }
        }
        
        stage('Security Scan') {
            steps {
                 echo 'Performing security scan with Snyk Code'
            }
            post {
                success {
                    script {
                        archiveArtifacts artifacts: '**/*', excludes: ''
                        mail to: "duyng2311@gmail.com",
                             subject: "Jenkins Security Scan Notification - ${currentBuild.currentResult}",
                             body: "The Security Scan stage has completed with status: ${currentBuild.currentResult}.",
                             attachmentsPattern: '**/target/*.log'
                    }
                }
                failure {
                    script {
                        archiveArtifacts artifacts: '**/*', excludes: ''
                        mail to: "duyng2311@gmail.com",
                             subject: "Jenkins Security Scan Notification - ${currentBuild.currentResult}",
                             body: "Security scan failed. ${currentBuild.currentResult}.",
                             attachmentsPattern: '**/target/*.log'
                    }
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