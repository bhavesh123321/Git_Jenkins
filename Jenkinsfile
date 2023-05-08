pipeline{
agent any
stages {
    stage('Build'){
    steps{
        echo "Building using maven"
    }}
    
stage('Unit and Integration Tests'){
    steps{
           echo "testing using JUnit"
    }
}

stage('Code Analysis'){
    steps{
         echo "Code analysis using CheckStyle"
    }
}

stage('Security Scan'){
    steps{
        echo "Security scan completed using Tenable"
    }
    post{
    success{ emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Security Scan status',
                body: 'The Security Scan has succeeded',
                
            )}
failure{emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Security Scan status',
                body: 'The Security Scan has failed.',
                
            )}}}
        
stage('Deploy to staging'){
    steps{
        echo "deploy to a staging server AWS EC2  server"
    }
}

stage('Integration Tests on Staging'){
    steps{
        echo "testing on staging environment using selenium"
    }}
}

stage('Deploy to Production'){
    steps{
        echo "deploy to a staging server Azure server
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
