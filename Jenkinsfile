pipeline {
    agent any
    stages {
      stage ('Compile Stage') {

        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn clean compile'
          }
        }
      }
      stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh 'mvn test'
          }
        }
      }
    }
}
