pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/emmalujosephwork/SIT753.git'
        RECIPIENT_EMAIL = 'emmalujosephwork@gmail.com'  // Your email
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code from GitHub"
                git branch: 'main', url: "${REPO_URL}"
            }
        }

        stage('Build') {
            steps {
                echo "Building the project (for static files this is a placeholder)"
                // If you have a build tool, you can specify it here (e.g., npm build or Maven build)
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests"
                // If you have tests, add commands to run them (e.g., npm test, JUnit)
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Running code analysis"
                // If you're using a tool like SonarQube, you can integrate it here
            }
        }

        stage('Security Scan') {
            steps {
                echo "Performing security scan"
                // Add security scanning tools (like OWASP Dependency Check or Snyk)
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging server"
                // Add your staging deployment commands (e.g., AWS CLI, Docker)
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging"
                // Add integration test commands here
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying to production server"
                // Add your production deployment commands here (e.g., AWS CLI)
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: Jenkins Pipeline - ${currentBuild.fullDisplayName}",
                body: """\
Hello,

The Jenkins pipeline for job "${env.JOB_NAME}" completed successfully.

You can view the build details here: ${env.BUILD_URL}

Best regards,
Jenkins
""",
                to: "${RECIPIENT_EMAIL}"
            )
        }
        failure {
            emailext(
                subject: "FAILURE: Jenkins Pipeline - ${currentBuild.fullDisplayName}",
                body: """\
Hello,

The Jenkins pipeline for job "${env.JOB_NAME}" has failed.

Please check the build details here: ${env.BUILD_URL}

Best regards,
Jenkins
""",
                to: "${RECIPIENT_EMAIL}"
            )
        }
    }
}
