pipeline {
    agent any

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Building the application using Maven...'
                // Uncomment the next line if Maven is installed
                bat 'mvn clean package'
            }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests with JUnit/TestNG...'
                bat 'mvn test'       // Run unit tests
                bat 'mvn verify'     // Run integration tests
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
                // bat 'mvn sonar:sonar -Dsonar.projectKey=YourProjectKey -Dsonar.host.url=http://your-sonarqube-server -Dsonar.login=your-token'
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency Check...'
                // bat 'dependency-check.bat --scan ./ --format HTML --out reports/'
            }
        }

        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server (AWS EC2)...'
                // bat 'scp target/app.jar ec2-user@staging-server:/home/ec2-user/app.jar'
            }
        }

        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in staging environment...'
                // bat './staging-tests.bat'
            }
        }

        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server (AWS EC2)...'
                // bat 'scp target/app.jar ec2-user@production-server:/home/ec2-user/app.jar'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finibated. Cleaning up workspace if necessary.'
            // cleanWs()  // Uncomment to clean workspace after build
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check console output for details.'
        }
    }
}
