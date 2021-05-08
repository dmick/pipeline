pipeline {
  agent any
  stages {
    stage('x86') {
      parallel {
        stage('x86') {
          steps {
            echo "${env.BUILD_ID} x86"
          }
        }

        stage('aarch64') {
          steps {
            echo '"${env.JOB_NAME} aarch64"'
          }
        }

      }
    }

    stage('join') {
      steps {
        echo "both builds done"
      }
    }

  }
}