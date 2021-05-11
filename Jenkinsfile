pipeline {
  agent any
  stages {
    stage('x86') {
      parallel {
        stage('x86') {
          steps {
            build job: 'ceph-grafana', parameters: [string(name: 'BRANCH', value: 'wip-grafana-container'), string(name: 'ARCH', value: 'x86_64')]
          }
        }

        stage('aarch64') {
          steps {
            build job: 'ceph-grafana', parameters: [string(name: 'BRANCH', value: 'wip-grafana-container'), string(name: 'ARCH', value: 'arm64')]
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
