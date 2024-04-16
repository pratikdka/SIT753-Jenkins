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
                    success {
                        emailext attachLog: true, 
                        body: 'Unit and Integration Tests passed successfully.', 
                        subject: 'Unit and Integration Tests Passed', 
                        from: 'pratik.khadka18@gmail.com',
                        to: 'pratik.khadka18@gmail.com'
                    }
                    failure {
                        emailext attachLog: true,
                        body: 'Unit and Integration Tests failed. See attached logs.', 
                        subject: 'Unit and Integration Tests Failed', 
                        from: 'pratik.khadka18@gmail.com',
                        to: 'pratik.khadka18@gmail.com'
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
                    success {
                        emailext attachLog: true, 
                        body: 'Security Scan passed successfully.', 
                        subject: 'Security Scan Passed', 
                        from: 'pratik.khadka18@gmail.com',
                        to: 'pratik.khadka18@gmail.com'
                    }
                    failure {
                        emailext attachLog: true, 
                        body: 'Security Scan failed. See attached logs.', 
                        subject: 'Security Scan Failed', 
                        from: 'pratik.khadka18@gmail.com',
                        to: 'pratik.khadka18@gmail.com'
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
