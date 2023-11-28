pipeline {
    agent any
    environment {
      DOCKERHUB_CREDENTIALS = credentials('dockerhub')
      mvn = tool 'apache-maven-3.8.6';
    }
    stages {
     /*stage ('Testing Stage') {
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
            sh 'ssh devops@172.174.206.242 "minikube stop"'
            sh 'ssh devops@172.174.206.242 "minikube start"'
            sh 'ssh devops@172.174.206.242 "export PUERTO_A_USAR=$(kubectl get services | grep -oP '$/\/$d+:(\\d+)' | cut -d':' -f2)"'
            sh 'ssh devops@172.174.206.242 "kubectl port-forward --address 0.0.0.0 svc/app $PUERTO_A_USAR:80"
            sh 'ssh devops@172.174.206.242 "echo $PUERTO_A_USAR"'
         }
     }
  }
}
