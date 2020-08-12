pipeline {
  agent any

  tools {nodejs 'NodeJS 4.8.6'
  }
  stages {
    stage('build') {
      steps {
        echo 'This is the build job'
        sh 'npm install'
      }
    }
    stage('test') {
      steps {
        echo 'This is the test job'
        sh 'npm test'
      }
    }
    stage('package') {
      steps {
        echo 'This is the package job'
        sh 'npm run package'
      }
    }
  }
  
  post{
    always{
      echo 'The pipeline has been completed'
    }
  }
}
