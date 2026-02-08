pipeline{
    agent any
     
    
    stages{
        stage("Install dependencies"){
             steps{
                bat "npm install"
            }
           
        }
        stage("Testing"){
            parallel{
                stage("Security Testing"){
                    steps{
                        bat "npm audit --audit-level=high"
                    }
                }
                stage("Run uI Testing"){
                    steps{
                        bat "npm run test"
                    }
                }
            }
        }
       

}}