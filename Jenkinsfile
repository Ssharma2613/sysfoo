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
        sh '''#Truncate the git_commit to the first 7 caharacters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT |cut -c 1-7)

#set the version using maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
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