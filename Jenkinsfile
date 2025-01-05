pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    
                        try {
                            publishChecks actions: [label: "build", identifier : "build" ] name: 'Build', conclusion: 'SUCCESS'
                            sh 'echo "Building the app..."'
                            
                        } catch (Exception e) {
                            publishChecks actions: [label: "build", identifier : "build" ] name: 'Build', conclusion: 'FAILURE'
                            error("Build failed!")
                        }
                    
                }
            }
        }
    }
}
