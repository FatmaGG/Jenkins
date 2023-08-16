pipeline {
  agent any 
 environment{
      CREDENTIALS = credentials('dockerhup')
    }
  stages {
    stage  ("Install dependeincies") {
      agent {
        docker {image 'node:lts-buster-slim'}
      }
      steps {
        sh 'pwd'
        sh 'ls'
        sh 'npm install'
      }
    }
    stage ("Test"){
      agent {
        docker {image 'node:lts-buster-slim'}
      }
      steps{
        sh 'npm run test'
      }
    }

    stage ("Build"){
      agent {
        docker {image 'node:lts-buster-slim'}
      }
      steps{
        sh 'npm run build'
      }
    }  
   stage("docker build"){
      steps { 
       sh 'docker build -t fatmagamal/jenkins-demo:latest .'
      }
    }
    stage ("LoginANDPushImage"){
   steps {
     sh 'echo username = ${DEOCKERHUB_CREDENTIALS_USR}'
    sh 'echo passwrod = ${DEOCKERHUB_CREDENTIALS_PSW}'  
     sh 'docker login -u ${DEOCKERHUB_CREDENTIALS_USR} -p ${DEOCKERHUB_CREDENTIALS_PSW} '  
     sh 'docker push fatmagamal/jenkins-demo:latest' 
     }
   }
  }
}
