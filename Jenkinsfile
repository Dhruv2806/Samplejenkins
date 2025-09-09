pipeline {
    agent any

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Building the application using Maven...'
                // Uncomment the next line if Maven is installed
                sh 'mvn clean package'
            }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests with JUnit/TestNG...'
                sh 'mvn test'       // Run unit tests
                sh 'mvn verify'     // Run integration tests
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
                // sh 'mvn sonar:sonar -Dsonar.projectKey=YourProjectKey -Dsonar.host.url=http://your-sonarqube-server -Dsonar.login=your-token'
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency Check...'
                // sh 'dependency-check.sh --scan ./ --format HTML --out reports/'
            }
        }

        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server (AWS EC2)...'
                // sh 'scp target/app.jar ec2-user@staging-server:/home/ec2-user/app.jar'
            }
        }

        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in staging environment...'
                // sh './staging-tests.sh'
            }
        }

        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server (AWS EC2)...'
                // sh 'scp target/app.jar ec2-user@production-server:/home/ec2-user/app.jar'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished. Cleaning up workspace if necessary.'
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
