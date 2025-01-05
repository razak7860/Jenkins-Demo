pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    
                        try {
                            publishChecks name: 'Jenkins/SBXDEPLOY Deploy', status: 'COMPLETED', title: 'Cleanup', conclusion: 'SUCCESS'
                            sh 'echo "Building the app..."'
                            
                        } catch (Exception e) {
                            publishChecks name: 'Jenkins/SBXDEPLOY Deploy', status: 'COMPLETED', title: 'Cleanup', conclusion: 'FAILED'
                            error("Build failed!")
                        }
                    
                }
            }
        }
    }
}
