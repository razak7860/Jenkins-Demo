pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                githubStatus context: "Build", description: "Building...", state: "pending" // Set pending status
                try {
                    echo "Building..."
                    sh 'echo "Simulating a build"'
                    githubStatus context: "Build", description: "Build successful", state: "success" // Set success status
                } catch (err) {
                    githubStatus context: "Build", description: "Build failed", state: "failure" // Set failure status
                    throw err // Re-throw the error to fail the build
                }
            }
        }
        stage('Test') {
            steps {
                githubStatus context: "Test", description: "Testing...", state: "pending" // Set pending status
                try {
                    echo "Testing..."
                    sh 'echo "Simulating tests"'
                    githubStatus context: "Test", description: "Tests passed", state: "success" // Set success status
                } catch (err) {
                    githubStatus context: "Test", description: "Tests failed", state: "failure" // Set failure status
                    throw err // Re-throw the error to fail the build
                }
            }
        }
        stage('Post-Merge Actions') {
            when {
                expression {
                    return env.BRANCH_NAME == 'main'
                }
            }
            steps {
                echo "Running post-merge actions on main..."
                // Your post-merge actions here (e.g., deployment)
                sh 'echo "Simulating deployment"'
            }
        }
    }
    post {
        always {
            echo "Build finished."
        }
    }
}