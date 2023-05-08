pipeline{
agent any
stages {
    stage('Build'){
    steps{
        echo "Build the code using maven."
    }
   }
    
stage('Unit and Integration Tests'){
    steps{
        echo "running unit Integration testing using Informatica" 
    }
}

stage('Code Analysis'){
    steps{
        echo "check the quality of the code as per industry standards using CheckStyle"
    }
}

stage('Security Scan'){
    steps{
        echo "security scan on the code using ausing Nmap"
    }
    post{
    success{ emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Security Scan status',
                body: 'The Security Scan has succeeded. Please check the logs for details.',
                
            )}
failure{emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Security Scan status',
                body: 'The Security Scan has failed. Please check the logs for details.',
                
            )}}}
        
stage('Deploy to staging'){
    steps{
        echo "deploy the application to a staging server AWS EC2 instance server"
    }
}

stage('Integration Tests on Staging'){
    steps{
        echo "testing on staging using Informatica"
    }
    post{
    success{ emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Integration Tests status',
                body: 'The Integration Tests has succeeded. Please check the logs for details.',
                
            )
     }
failure{emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Integration Tests status',
                body: 'The Integration Tests has failed. Please check the logs for details.',
                
            )}}
}

stage('Deploy to Production'){
    steps{
        echo "deploy to production server AWS EC2 instance server"
    }
}}
post {
        success {
            emailext (
                attachLog: true, 
                to: 'bhaveshagg2028@gmail.com',
                subject: 'Pipeline succeeded',
                body: 'The pipeline has succeeded. Please check the logs for details.',
                
            )
        }

        failure {
            emailext (
                subject: "Pipeline is Failed",
                body: "The pipeline has failed. See attached logs.",
                to: "bhaveshagg2028@gmail.com",
                attachLog: true,
            )
        }
    }
}
