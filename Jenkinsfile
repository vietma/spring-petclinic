pipeline {
  agent any
  tools {
    maven 'Maven3.5.4'
  }
  stages {
    stage('Clean') {
      steps {
        sh 'mvn clean'
      }
    }

    stage('Compile') {
      steps {
        sh 'mvn -B compile'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn -B test'
      }
    }
  }
}
