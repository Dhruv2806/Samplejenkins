pipeline {
    agent any

    tools {
        // Make sure these are configured in Jenkins Global Tool Configuration
        maven 'Maven3'    // Your Maven installation name
        jdk 'JDK17'       // Your JDK installation name
    }

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                dir('my-app') {
                    echo 'Building the application using Maven...'
                    bat 'mvn clean package'
                }
            }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                dir('my-app') {
                    echo 'Running unit and integration tests with Maven...'
                    bat 'mvn test'       // Run unit tests
                    bat 'mvn verify'     // Run integration tests
                }
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                dir('my-app') {
                    echo 'Analyzing code quality with SonarQube...'
                    // bat 'mvn sonar:sonar -Dsonar.projectKey=YourProjectKey -Dsonar.host.url=http://your-sonarqube-server -Dsonar.login=your-token'
                }
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                dir('my-app') {
                    echo 'Running security scan using OWASP Dependency Check...'
                    // bat 'dependency-check.bat --scan ./ --format HTML --out reports/'
                }
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
            echo 'Pipeline finished. Cleaning up workspace if necessary.'
            // cleanWs()  // Uncomment if you want to clean workspace
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check console output for details.'
        }
    }
}
