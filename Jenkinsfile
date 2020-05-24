pipeline {
  agent {
    node {
      label 'Node1'
    }

  }
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/Roberto-devops/simple-java-maven-app.gitz', branch: 'master', credentialsId: 'roberto-devops')
      }
    }

    stage('') {
      steps {
        sh 'cat jenkins/Jenkinsfile'
      }
    }

  }
}