pipeline {
  agent {
    docker {
      image 'node:lts-buster-slim'
    }
  }
  stages {
    stage  ("Install dependeincies") {
      steps {
        sh 'pwd'
        sh 'ls'
        sh 'npm install'
      }
    }
    stage ("Test"){
      steps{
        sh 'npm run test'
      }
    }

    stage ("Build"){
      steps{
        sh 'npm run build'
      }
    }  
   stage("docker build"){
      steps { 
       sh 'docker build . -t fatmagamal/jenkins-demo:latest '
      }
    }
  }
}
