pipeline {
    agent any

    stages {
        stage('Build PR') {
            when {
                expression { 
                    return env.BRANCH_NAME.startsWith('PR-') 
                }
            }
            steps {
                echo "Building Pull Request: ${env.BRANCH_NAME} "
            }
        }
        stage('Build Develop') {
            when {
                expression {
                    return env.BRANCH_NAME.startsWith('PR')
                }
            }
            steps {
                echo "Building PR Branch and learning Jenkins"
            }
        }
        stage('Build Main') {
            when {
                branch 'main'
            }
            steps {
                echo "Building Main Branch"
            }
        }
    }

    
}
