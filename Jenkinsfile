pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    withChecks(name: 'Build Process') {
                        try {
                            sh 'echo "Building the app..."'
                            publishChecks name: 'Build', conclusion: 'success', output: [
                                title: 'Build Success',
                                summary: 'The application was built successfully.'
                            ]
                        } catch (Exception e) {
                            publishChecks name: 'Build', conclusion: 'failure', output: [
                                title: 'Build Failed',
                                summary: 'The build process encountered errors.',
                                text: "Error: ${e.message}"
                            ]
                            error("Build failed!")
                        }
                    }
                }
            }
        }
    }
}
