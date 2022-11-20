pipeline {
    agent any
    
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
         }
        stage('Sonarqube') {
          environment {
                scannerHome = tool 'SonarQubeScanner'
        } 
            steps {
                withSonarQubeEnv('sonarqube') {
                   sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
            }
        } 
    }
}   
