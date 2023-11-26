pipeline {
    agent any
      stage ('Testing Stage') {
        steps {
          withMaven(maven : 'apache-maven-3.9.5') {
            sh '-X compile test'
          }
        }
      }
}
