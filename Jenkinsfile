pipeline{
    agent any
     
    
    stages{
        stage("Install dependencies"){
             steps{
                bat "npm install"
            }
           
        }
        stage("Run npm security"){
             steps{
                bat "npm audit fix"
            }
        }
        stage("Run tests"){
             steps{
                bat "npm test"
            }
        }
    }

}