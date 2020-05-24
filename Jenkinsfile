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

    stage('Test ') {
      steps {
        sh 'mvn test'
        junit(allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml', healthScaleFactor: 2)
      }
    }

    stage('Sonar') {
      steps {
        sh 'mvn sonar:sonar -Dsonar.projectKey=test -Dsonar.host.url=http://192.168.10.20:8080 -Dsonar.login=fc1ad35ec36960396cb0ba7a20ef6c209cc5f2fd -Dsonar.junit.reportPaths=target/surefire-reports/*.xml'
      }
    }

  }
}