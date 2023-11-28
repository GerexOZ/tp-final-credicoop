pipeline {
    agent any
    environment {
      DOCKERHUB_CREDENTIALS = credentials('dockerhub')
      mvn = tool 'apache-maven-3.8.6';
    }
    stages {
    /* stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.8.6') {
            sh 'mvn -X test'
          }
        }
      }
     stage('SonarQube Analysis') {
       steps {
         withSonarQubeEnv('sonarqube') {
         sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=TPFinalCredicoop -Dsonar.projectName='TPFinalCredicoop'"
         }
       }
     }
     stage('Build Docker Image') {
        steps {
              sh '/usr/bin/docker build -t gereoz/jenkins-docker-hub .'
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
     stage('Delete image from VM1-Infraestructura') {
       steps {
         sh 'docker image rm gereoz/jenkins-docker-hub'
       }
     }*/
     stage('test'){
       steps {
         sh 'echo $USER'  
       }
     }
  }
}
