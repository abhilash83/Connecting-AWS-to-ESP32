pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building ${env.BRANCH_NAME}"
                sh 'npm install'   // or mvn clean install, gradle build, etc.
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'npm test'
            }
        }
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying main branch"
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline successful for ${env.BRANCH_NAME}"
        }
        failure {
            echo "❌ Pipeline failed for ${env.BRANCH_NAME}"
        }
    }
}
