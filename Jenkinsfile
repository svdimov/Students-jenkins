pipeline {
  agent any

  stages {
    stage('Install dependencies') {
      steps { bat 'npm install' }
    }

    stage('Testing') {
      failFast true
      parallel {
        stage('Security Testing') {
          steps {
            bat 'npm audit fix --force'
          }
        }

        stage('Run UI Testing') {
          steps {
            bat 'npm run test'
          }
        }
      }
    }
  }
}
