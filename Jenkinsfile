pipeline {
  agent none
  stages {
    stage('build') {
      agent {
        docker {
          image 'schoolofdevops/node:4-alpine'
        }

      }
      steps {
        echo 'This is the build job'
        sh 'npm install'
      }
    }

    stage('test') {
      agent {
        docker {
          image 'schoolofdevops/node:4-alpine'
        }

      }
      steps {
        echo 'This is the test job'
        sh '''npm install




npm test'''
      }
    }

    stage('package') {
      agent {
        docker {
          image 'schoolofdevops/node:4-alpine'
        }

      }
      steps {
        echo 'This is the package job'
        sh '''npm install 
npm run package'''
        archiveArtifacts '**/distribution/*.zip'
      }
    }

    stage('docker build and publish') {
      steps {
        script {

          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("chato973/frontend:v${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
          }
        }

      }
    }

  }
  tools {
    nodejs 'NodeJS 4.8.6'
  }
  post {
    always {
      echo 'The pipeline has been completed'
    }

  }
}