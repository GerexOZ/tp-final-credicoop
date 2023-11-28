pipeline {
    agent any
    environment {
      DOCKERHUB_CREDENTIALS = credentials('dockerhub')
      mvn = tool 'apache-maven-3.9.5';
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
       steps {
         withSonarQubeEnv('sonarqube') {
         sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=TPFinalCredicoop -Dsonar.projectName='TPFinalCredicoop'"
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
     stage('Conectar con la VM de produccion mediante SSH'){
         sh 'ssh devops@172.174.206.242'
         sh 'cd kompose'
         sh 'echo pwd'
    }
  }
}


/*
  echo "$DOCERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
            docker build -t ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest .
            docker push ${DOCKERHUB_USERNAME}/$IMAGE_NAME:latest
final
*/
