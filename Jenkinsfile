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
                script { // This is the crucial addition
                    githubNotify context: "Build", description: "Building...", status: "PENDING"
                    try {
                        echo "Building..."
                        sh 'echo "Simulating a build"'
                        githubNotify context: "Build", description: "Build successful", status: "SUCCESS"
                    } catch (err) {
                        githubNotify context: "Build", description: "Build failed", status: "FAILURE"
                        throw err
                    }
                } // End of script block
            }
        }
        stage('Test') {
            steps {
                script { // This is the crucial addition
                    githubNotify context: "Test", description: "Testing...", status: "PENDING"
                    try {
                        echo "Testing..."
                        sh 'echo "Simulating tests"'
                        githubNotify context: "Test", description: "Tests passed", status: "SUCCESS"
                    } catch (err) {
                        githubNotify context: "Test", description: "Tests failed", status: "FAILURE"
                        throw err
                    }
                } // End of script block
            }
        }
        stage('Post-Merge Actions') {
            when {
                expression { return env.BRANCH_NAME == 'main' }
            }
            steps {
                echo "Running post-merge actions on main..."
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