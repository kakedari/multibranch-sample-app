pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        echo "Build"
      }
    }
  }
  post {
    always {
        junit(
          allowEmptyResults: true, 
          testResults: '**/build/test-results/test/*.xml'
        )
        recordIssues(
          enabledForFailure: true, aggregatingResults: true, 
          tools: [java(), checkStyle(pattern: '**/build/**/main.xml', reportEncoding: 'UTF-8')]
        )
    }
  }
}
