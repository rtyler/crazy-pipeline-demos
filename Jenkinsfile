#!/usr/bin/env groovy

properties([pipelineTriggers([cron('*/10 * * * *')])])

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
