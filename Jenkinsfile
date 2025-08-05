pipeline {
    agent any
    environment {
        NODE_VERSION = '18.x'
    }
    tools {
        nodejs "${NODE_VERSION}"
    }
    stages {
        stage{'Checkout'}{
            steps { 
                checkout scm
            }
        }
        stage {'Install dependencies'}{
            steps {
                if (isunix()){
                    sh 'npm install'
                } else {
                    sh 'npm install'
                }
                
            }
        }
        stage {'start application and run tests'}{
            steps {
                script {
                    sh 'npm start &'
                    sh  'wait-on http://localhost:8090'
                    sh 'npm test'
                }
            }
        }
    }
    post {
        always {
            echo 'CI pipeline completed'
        }
    }
}