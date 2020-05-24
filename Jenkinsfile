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

    stage('Sonar analyze') {
      steps {
        sh '''mvn sonar:sonar 
  -Dsonar.projectKey=test 
  -Dsonar.host.url=http://192.168.10.20:8080 \\
  -Dsonar.login=9166d51e52b45e6f64b7fe6905f6632111108ef9'''
      }
    }

  }
}