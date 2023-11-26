pipeline {
            stage ('Deploy to Testing Environment') {
                  steps {
                    container ('jdk') {
                      echo "deploy target/customer-portal*.war to testing environment"
                    }
                  }
                }
              }
