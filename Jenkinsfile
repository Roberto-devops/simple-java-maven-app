pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        git(url: 'https://github.com/jenkins-docs/simple-java-maven-app.git', branch: 'master', credentialsId: 'GitHubCR', poll: true)
      }
    }

  }
}