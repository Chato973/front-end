pipeline {
  agent any

  tools {nodejs 'NodeJS 4.8.6'
  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }
    stage('test') {
      steps {
        sh 'npm test'
      }
    }
    stage('package') {
      steps {
        sh 'npm run package'
      }
    }
  }
}
