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
                script {
                    publishChecks name: "Build", status: "PENDING", conclusion: "Building..."
                    try {
                        echo "Building..."
                        sh 'echo "Simulating a build"'
                        publishChecks name: "Build", status: "COMPLETED", conclusion: "Build successful"
                    } catch (err) {
                        publishChecks name: "Build", status: "FAILURE", conclusion: "Build failed"
                        throw err
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script { // This is the crucial addition
                    withChecks(name: 'test') {
                    sh 'echo "Simulating Testing"'
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
            echo "Build finished.........................."
        }
    }
}