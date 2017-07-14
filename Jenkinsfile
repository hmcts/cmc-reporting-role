#!groovy

@Library('Reform') _

node {
  ws('payment-reconciliation-role') { // This must be the name of the role otherwise ansible won't find the role
    try {
      wrap([$class: 'AnsiColorBuildWrapper', colorMapName: 'xterm']) {
        stage('Checkout') {
          checkout scm
        }

        stage('Start containers') {
          sh '''
          molecule create
        '''
        }

        stage('Run role') {
          sh '''
          molecule converge
        '''
        }

        stage('Check idempotent') {
          sh '''
          molecule idempotence
        '''
        }

        stage('Run tests') {
          sh '''
          molecule syntax
          molecule verify
        '''
        }
      }

    } catch (err) {
      notifyBuildFailure channel: '#cmc-tech-notification'
      throw err
    } finally {
      stage('Cleanup') {
        sh '''
          molecule destroy
        '''
      }
      deleteDir()
    }
  }
}
