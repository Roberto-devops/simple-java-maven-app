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
        withSonarQubeEnv(installationName: 'my_custom_sonar', credentialsId: 'sonar_token') {
          sh 'mvn sonar:sonar -Dsonar.projectKey=test   -Dsonar.surefire.reportsPath=target/surefire-reports/*.xml'
        }

      }
    }

  }
}