pipeline {
    agent any
    tools {
        maven 'Maven-3.9.11'   
        jdk 'JDK17'           
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the application using Maven...'
                bat 'cd my-app && mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests with Maven...'
                bat 'cd my-app && mvn test'
                bat 'cd my-app && mvn verify'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
                // For Windows, if SonarQube scanner is installed:
                // bat 'mvn sonar:sonar -Dsonar.projectKey=YourProjectKey -Dsonar.host.url=http://your-sonarqube-server -Dsonar.login=your-token'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan (e.g., OWASP Dependency Check)...'
                // bat 'dependency-check.bat --scan ./ --format HTML --out reports/'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging...'
                // Example with Windows tools:
                // bat 'scp target\\app.jar user@staging-server:/home/user/app.jar'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in staging environment...'
                // bat 'staging-tests.bat'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production...'
                // bat 'scp target\\app.jar user@production-server:/home/user/app.jar'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished. Cleaning up workspace if necessary.'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check console output for details.'
        }
    }
}
