pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build the code using Maven to compile and package the application.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    try {
                        echo 'Run unit tests (JUnit) to verify functionality.'
                        echo 'Run integration tests (JUnit + Maven Surefire/Failsafe) to verify components work together.'
                        // Put your actual test commands here
                    } catch (err) {
                        currentBuild.result = 'FAILURE'
                        throw err
                    }
                }
            }
            post {
                always {
                    emailext(
                        to: 'dhruvvmaheta2006@gmail.com',
                        subject: "Unit & Integration Tests - ${currentBuild.currentResult}",
                        body: """Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}
                        Check console output at: ${env.BUILD_URL}""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyze code quality using SonarQube.'
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    try {
                        echo 'Scan for vulnerabilities using OWASP Dependency-Check.'
                        // Put your security scan command here
                    } catch (err) {
                        currentBuild.result = 'FAILURE'
                        throw err
                    }
                }
            }
            post {
                always {
                    emailext(
                        to: 'dhruvvmaheta2006@gmail.com',
                        subject: "Security Scan - ${currentBuild.currentResult}",
                        body: """Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}
                        Security scan completed. Check details at: ${env.BUILD_URL}""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploy application to AWS EC2 (staging environment).'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests in staging environment to validate production-like setup.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploy application to AWS EC2 (production environment).'
            }
        }
    }
}
