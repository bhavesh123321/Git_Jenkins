pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
               echo "Building using maven"
            }
        }
        stage('Unit and Integration Tests') {
           
            steps {
                echo "testing using JUnit"
            }
        }
        stage('Code Analysis') {
            
            steps {
               echo "Code analysis using CheckStyle"
            }
        }
        stage('Security Scan') {
           
            steps {
                echo "Security scan completed using Tenable"
            }
        }
        stage('Deploy to Staging') {
                       steps {
                echo "Deployed to staging using Azure VM"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Testing uisng JUnit "
            }
            post{success {
            emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Pipeline succeeded',
                body: 'Testing succeeded, check the logs',
                
            )
        }
        failure {
            emailext (
                subject: "Pipeline is Failed",
                body: 'Testing failed check the logs',
                to: "bhaveshagg2028@gmail.com",
                attachLog: true,
            )
        }
    }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy the application to a production server Azure instance server"
                }
            }
        }
    }
    
    post {
        
        success {
            emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Pipeline succeeded',
                body: 'pipeline succeeded, check the logs',
                
            )
        }

        failure {
            emailext (
                subject: "Pipeline is Failed",
                body: 'pipeline failed check the logs',
                to: "bhaveshagg2028@gmail.com",
                attachLog: true,
            )
        }
    }
}
