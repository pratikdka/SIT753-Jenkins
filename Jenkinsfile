pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project using Maven as building tool...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using Maven JUnit tests...'
            }
            post {
                success{
                    emailext body: 'Unit and Integration Tests Status', subject: 'Unit and Integration Tests has Passed', to: 'pratik.khadka18@gmail.com'
                }
                failure{
                    emailext body: 'Unit and Integration Tests Status', subject: 'Unit and Integration Tests has Failed', to: 'pratik.khadka18@gmail.com'
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
                echo 'Performing security scan using OWASP for Dependency Check...'
            }
            post {
                success{
                    emailext body: 'Security Scan', subject: 'Security Scan has Passed', to: 'pratik.khadka18@gmail.com'
                }
                failure{
                    emailext body: 'Security Scan', subject: 'Security Scan has Failed', to: 'pratik.khadka18@gmail.com'
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
