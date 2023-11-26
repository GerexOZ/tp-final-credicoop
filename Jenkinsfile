pipeline {
    agent any
    stages {
      stage ('Compile Stage') {

        steps {
          withMaven(maven : 'apache-maven-1.4.1') {
            bat'mvn clean compile'
          }
        }
      }
      stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-1.4.1') {
            bat'mvn test'
          }
        }
      }
    }
}
