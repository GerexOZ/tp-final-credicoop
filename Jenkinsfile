pipeline {
    agent {
        docker {
            image ''
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
     /* stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn test'
          }
        }
      }*/
      stage('Build') {
        steps {
          script {
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        docker.build('gereoz/jenkins-docker-hub')
                    }
           }
        }
      }
     /* stage('Login') {
        steps {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        }
      }
      /*stage('Push') {
        steps {
          sh 'docker push gereoz/jenkins-docker-hub'
        }
      }*/
    }
}


/*
  echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
            docker build -t ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest .
            docker push ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest

*/
