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
                echo 'Run unit tests (JUnit) to verify functionality.'
                echo 'Run integration tests (JUnit + Maven Surefire/Failsafe) to verify components work together.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyze code quality using SonarQube.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Scan for vulnerabilities using OWASP Dependency-Check.'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploy application to AWS EC2 (staging environment).'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                //echo 'Run integration tests in staging environment to validate production-like setup.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploy application to AWS EC2 (production of environment).'
            }
        }
    }
}
