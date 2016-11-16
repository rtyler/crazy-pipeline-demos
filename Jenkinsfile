#!/usr/bin/env groovy

node('docker') {
    stage('Build') {
        docker.image('alpine').inside {
            echo 'im building'
            sh 'uname -a'
        }
    }

    stage('Test') {
        sleep 10
    }

    stage('Deploy') {
    }
}
