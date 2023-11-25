node {
  stage('SCM') {
    checkout scm
  }
stage('SonarQube Analysis') {
    def mvn = tool 'libros';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -X -Dsonar.projectKey=testlibros -Dsonar.projectName='testlibros'"
    }
  }
}
