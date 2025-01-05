pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    
                        try {
                            publishChecks name: 'Build', conclusion: 'SUCCESS'
                            sh 'echo "Building the app..."'
                            
                        } catch (Exception e) {
                            publishChecks name: 'Build', conclusion: 'FAILURE'
                            error("Build failed!")
                        }
                    
                }
            }
        }
    }
}
