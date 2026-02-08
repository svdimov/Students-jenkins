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
            catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
              bat 'npm audit'
            }
          }
        }
        stage('Run UI Testing') {
          steps { bat 'npm run test' }
        }
      }
    }
  }
}
