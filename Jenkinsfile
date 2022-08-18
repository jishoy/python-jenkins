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
    
    stage("Pushing to AWS Ecr"){
      steps {
         script{
          docker.withRegistry('https://528671083836.dkr.ecr.us-west-1.amazonaws.com', 'ecr:us-west-1:aws-ecr'){
            dockerImage.push(image + "${env.BUILD_NUMBER}")
            dockerImage.push("latest")
          }
         }
      }
    }
        
  
  }
}
