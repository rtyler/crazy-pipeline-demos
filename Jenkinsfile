#!/usr/bin/env groovy

node('docker') {
    docker.image('alpine').inside {
        sh 'uname -a'
    }
}
