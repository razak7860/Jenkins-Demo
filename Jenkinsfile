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
                githubNotify context: "Build", description: "Building...", status: "PENDING" // Set pending status
                step {
                    try {
                    echo "Building..."
                    sh 'echo "Simulating a build"'
                    githubNotify context: "Build", description: "Build successful", status: "SUCCESS" // Set success status
                } catch (err) {
                    githubNotify context: "Build", description: "Build failed", status: "FAILURE" // Set failure status
                    throw err // Re-throw the error to fail the build
                }
            }
        }
        stage('Test') {
            steps {
                githubNotify context: "Test", description: "Testing...", status: "PENDING" // Set pending status
                step{
                    try {
                    echo "Testing..."
                    sh 'echo "Simulating tests"'
                    githubNotify context: "Test", description: "Tests passed", status: "SUCCESS" // Set success status
                    } catch (err) {
                        githubNotify context: "Test", description: "Tests failed", status: "FAILURE" // Set failure status
                        throw err // Re-throw the error to fail the build
                    }
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