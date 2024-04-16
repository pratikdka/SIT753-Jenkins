pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project using Maven as building tool...'     
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests using Maven JUnit tests...'
                }
                post {
                    always{
                        mail to: "pratik.khadka18@gmail.com",
                        subject: "Unit and Integration Test Results",
                        body: "Log has been attached!!"
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {    
                    echo 'Analyzing code quality using SonarQube for code Quality Analysis...'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan using OWASP for Dependency Check...'
                }
                post {
                    always{
                        mail to: "pratik.khadka18@gmail.com",
                        subject: "Security Scan Results",
                        body: "Log has been attached!!"
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging environment via shell script for AWS CLI...'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production server using AWS CLI...'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
