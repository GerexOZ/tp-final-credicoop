pipeline {
    agent any
    environment {
      registry = "gereoz/tpcredicoop"
      registryCredential = 'dockerhub_id'
      dockerImage = 'DockerfileRender'
    }
    stages {
      stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn test'
          }
        }
      }
      stage ('Build and Push Dockerfile') {
        steps {  
          sh "docker build -t gereoz/libros ."  
        }
      }
    }
}


/*
  echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
            docker build -t ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest .
            docker push ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest

*/
