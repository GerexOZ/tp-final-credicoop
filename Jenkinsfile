pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
     stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn -X test'
          }
        }
      }
      stage('SonarQube Analysis') {
        tools {
          jdk "java17" // the name you have given the JDK installation using the JDK manager (Global Tool Configuration)
        }
        environment {
          scannerHome = tool 'SonarQube Scanner' // the name you have given the Sonar Scanner (Global Tool Configuration)
        }
        steps {
          withSonarQubeEnv(installationName: 'sonarqube') {
            sh 'mvn sonar:sonar'
          }
        }
     }
     stage('Build Docker Image') {
        steps {
          script{
              sh '/usr/bin/docker build -t gereoz/jenkins-docker-hub .'
          }
        }
      }
     stage('Login') {
        steps {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        }
      }
     stage('Push') {
        steps {
          sh 'docker push gereoz/jenkins-docker-hub'
        }
      }
    }
}


/*
  echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
            docker build -t ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest .
            docker push ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest

*/
