pipeline {
  agent any
  options { 
    skipDefaultCheckout()
    timestamps()
  }
  parameters {
    string(name: 'GRAFANA_VERSION', defaultValue: '6.7.4-1')
    string(name: 'PIECHART_VERSION', defaultValue: '1.4.0')
    string(name: 'STATUS_PANEL_VERSION', defaultValue: '1.0.9')
  }

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
        sh "sudo podman manifest create ceph-grafana:"
      }
    }

  }
}
