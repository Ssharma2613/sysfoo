pipeline {
    agent any
    tools{
      maven 'Maven 3.9.9'
    }
    stages {
        stage('build') {
            steps {
                // Get some code from a GitHub repository
                echo 'compiling Sysfoo app'
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                echo 'running unit tests...'
                sh 'mvn clean test'
            }
        }
        
        stage('package'){
            steps{
                echo 'packaging the app...'
                sh 'mvn package -Dskiptests'
            }
        }
    }
        
    post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                always {
                    echo 'this pipeline is completed'
                }
            }
        
}
