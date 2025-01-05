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
                    withChecks(name: 'build', includeStage: true) {
                    sh 'echo "Simulating build process"'
}
                } // End of script block
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