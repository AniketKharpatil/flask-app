pipeline {
  agent any
  
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          docker.build("weather-app:${env.BUILD_ID}", "-f Dockerfile .")
        }
      }
    }
    
    stage('Run Docker Container') {
      steps {
        script {
          docker.run("weather-app:${env.BUILD_ID}", "-p 5000:5000")
        }
      }
    }
  }
  
  post {
    always {
      script {
        docker.stop("weather-app:${env.BUILD_ID}")
        docker.removeImage("weather-app:${env.BUILD_ID}")
      }
    }
  }
}
