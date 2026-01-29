pipeline {
    agent any
    
    options {
        timeout(time: 30, unit: 'MINUTES')
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                   
                    sh 'docker build -t shp-devops-back:${BUILD_NUMBER} .'
                    
                    sh 'docker tag shp-devops-back:${BUILD_NUMBER} shp-devops-back:latest'
                }
            }
            
        }
        
        stage('Cleanup') {
            steps {
                script {
                    
                    sh 'docker system prune -f || true'
                }
            }
        }
    }
    
}