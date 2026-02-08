pipeline {
    agent any

    stages {
        stage("Install Dependencies") {
            steps {
                bat 'npm install'
            }
        }

        stage("Testing") {
            failFast true
            parallel {
                stage("Run npm security") {
                    steps {
                        bat 'npm audit'
                    }
                }
                stage("Run UI Tests") {
                    steps {
                        bat 'npm test'
                    }
                }
            }
        }

        stage("Approval for Deployment") {
            steps {
                input message: 'Approve deployment to production?',
                      ok: 'Deploy to render'
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying application..."
            }
        }
    }
}