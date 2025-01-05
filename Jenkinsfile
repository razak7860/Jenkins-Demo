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
                    // Explicitly define the status check name using `withChecks`
                    withChecks(name: 'Build & Test', includeStage: true) {
                        // Simulate a build process
                        sh 'echo "Running build process..."'
                        sh 'exit 0' // Simulate success
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script { // This is the crucial addition
                    withChecks(name: 'test', includeStage: true) {
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