pipeline {
  agent {
    node {
      label 'Node1'
    }

  }
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/Roberto-devops/simple-java-maven-app.git', branch: 'master', credentialsId: 'roberto-devops')
      }
    }

    stage('build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }

  }
}