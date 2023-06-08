pipeline {
  environment {
    registry = "akenlavanya/demoimage"
    registryCredential = "docid"
    dockerImage = ""
  }
  agent any
  
  stages {
    stage('Build image') {
      steps {
        script {
          dockerImage = docker.build(registry + ":$BUILD_NUMBER")
        }
      }
    }
    stage('Deploy the image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
