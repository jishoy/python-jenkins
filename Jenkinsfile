pipeline {
  agent any
  environment  {
    image = "jishoy"
  }
  
  stages {
    stage("Clone the repository") {
      steps {
        git 'https://github.com/jishoy/python-jenkins.git'
        sh 'ls'
      }
    }
    
                
    stage("Building the Docker Image") {
      steps {
        script {
          dockerImage = docker.build image + ":$BUILD_NUMBER"
        }
      }
    }
    
  }
}
