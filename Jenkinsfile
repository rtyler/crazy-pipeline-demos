#!/usr/bin/env groovy

node('docker') {
    docker.image('alpine').inside {
        stage('Current Platform') {
            sh 'uname -a'
        }
        stage('Another thing') {
            sh 'printenv'
        }
    }
}
