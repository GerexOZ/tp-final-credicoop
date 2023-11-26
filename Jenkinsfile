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
      stage('Building our image') {
        steps{
          script {
            dockerImage = docker.build registry + ":$BUILD_NUMBER"
          }
        }
      }
      stage('Deploy our image') {
        steps{
          script {
            docker.withRegistry('', registryCredential) {
              dockerImage.push()
            }
          }
        }
      }
    }
}


/*
  echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
            docker build -t ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest .
            docker push ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest

*/
