pipeline {
    agent{
        dockerfile true
    }
    stages {
      stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn test'
          }
        }
      }
      stage ('Build Docker Image and Push it') {
          steps {
            def customImage = docker.build("gereoz/libros", "./DockerfileRender")
            customImage.push()
          }
      }    
    }
}


/*
  echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
            docker build -t ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest .
            docker push ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest

*/
