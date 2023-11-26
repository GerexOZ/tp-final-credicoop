pipeline {
    agent any
    stages {
      stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn test'
          }
        }
      }
      stage('Build image') {
            steps {
                echo 'Starting to build docker image'

                script {
                    def customImage = docker.build("my-image:${env.BUILD_ID}")
                    customImage.push()
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
