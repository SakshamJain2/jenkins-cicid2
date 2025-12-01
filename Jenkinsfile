pipeline {
  agent any 

    environment {
        IMAGE_NAME = "djangoapp"
        CONTAINER_NAME = "djangoapp"
        PORT = "8000"
    }
  stages {
    stage('checkout code'){
      steps{
          checkout scm  
      }
    }
    stage('build docker image'){
      steps{
        sh """
        echo 'building docker image'
        docker build -t djangoapp:1.0.0 .
        """
      }
    }
    stage('running new container'){
      steps{
      sh """
      echo "creating new container from image"
      docker run -d --name hello -p 8000:8000 djangoapp:1.0.0
      """
      }
    }

    
  }
  post {
    success{
      echo "deployment is succesful : djangapp:1.0.0"
    }
    failure {
      echo "deployment failed "
    }
  }

  
}
