node {
   stage('Get Source') {
      // copy source code from local file system and test
      // for a Dockerfile to build the Docker image
      git ('https://github.com/AniketKharpatil/flask-app')
      if (!fileExists("Dockerfile")) {
         error('Dockerfile missing.')
      }
   }
   stage('Build Docker') {
       // build the docker image from the source code using the BUILD_ID parameter in image name
         sh "sudo docker build -t weather-app ."
   }
   stage("run docker container"){
        sh "sudo docker run -d -p 8000:8000 weather-app"
    }
}
