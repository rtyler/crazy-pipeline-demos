#!/usr/bin/env groovy

node('docker') {
    stage('Build') {
        docker.image('alpine').inside {
            echo 'im building'
            sh 'uname -a'
        }
    }

    stage('Test') {
        docker.image('redis').withRun { container ->
            docker.image('maven').inside("--link ${container.id}:redis") {
                sh 'host redis'
                sh 'ls -lah'
            }
        }
    }

    stage('Deploy') {
    }
}
