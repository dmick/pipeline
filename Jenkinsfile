pipeline {
    agent any 
    stages {
        stage('x86') {
            steps {
                echo "${env.BUILD_ID} x86"
            }
	}
        stage('aarch64') {
            steps {
                echo "${env.JOB_NAME} aarch64"
            }
        }
    }
}
