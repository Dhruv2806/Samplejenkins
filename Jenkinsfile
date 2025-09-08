pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application using Maven...'
                // Example: sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests with JUnit...'
                // Example: sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
                // Example: sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency Check...'
                // Example: sh 'dependency-check.sh --scan .'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server (AWS EC2)...'
                // Example: sh 'scp target/app.jar ec2-user@staging-server:/app'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in staging environment...'
                // Example: sh './integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server (AWS EC2)...'
                // Example: sh 'scp target/app.jar ec2-user@prod-server:/app'
            }
        }
    }
}
