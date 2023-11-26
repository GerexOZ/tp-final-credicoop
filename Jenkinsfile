pipeline {
    agent any
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
      stage('Verificar Docker') {
            steps {
                script {
                    def dockerPath = sh(script: 'which docker', returnStdout: true).trim()
                    echo "La ruta de Docker es: ${dockerPath}"
                }
            }
        }
      /*stage('Build') {
        steps {
          sh 'docker build -t gereoz/jenkins-docker-hub .'
        }
      }*/
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
