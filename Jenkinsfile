pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compiling Sysfoo app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running unit tests...'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'packaging the app...'
        sh 'mvn package -Dskiptests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.9'
  }
  post {
    always {
      echo 'this pipeline is completed'
    }

  }
}