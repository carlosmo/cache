pipeline {
  agent {
    label 'master'
  }
  stages {
    stage('Checkout & Checks') {
      steps {
        // Check Files
        sh 'ls -l'
        // Version Checks
        sh 'python3 --version'
        sh 'gradle --version'
        sh 'kotlin -version'
        sh 'java -version'
        sh 'javac -version'
        // Chceking $PATH for ANDROID_HOME
        sh 'echo $ANDROID_HOME'
        // Chceking $PATH for JAVA_HOME
        sh 'echo $JAVA_HOME'
        
      }
    }
    stage('Build') {
      steps {
        dir("${env.WORKSPACE}/Cache/"){
          sh 'gradle build'
        }
      }
    }
    stage('run unit tests'){
      steps{
        dir("${env.WORKSPACE}/Cache"){
        }
      }
    }
    stage('run integration tests') {
      steps{
        dir("${env.WORKSPACE}/Cache"){
        }
      }
    }
  }
  post {
     always {
       echo 'Attempting to clean build directory'
       deleteDir()
     }
     success {
       echo 'success'
     }
     unstable {
       echo 'unstable'
     }
     failure {
       echo 'failed'
     }
     changed {
       echo 'following changes were detected in build -'
     }
  }
}
