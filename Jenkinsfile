node {
  stage('SCM') {
    checkout scm
  }
stage('SonarQube Analysis') {
    def mvn = tool 'libros';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -DXsonar.projectKey=testlibros -DXsonar.projectName='testlibros'"
    }
  }
}
