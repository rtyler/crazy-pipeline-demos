#!/usr/bin/env groovy

node('docker') {
    stage('Build') {
        docker.image('alpine').inside {
            echo 'im building'
            sh 'echo "HELLO" > artifact.txt'
        }
    }

    stage('Test') {
        docker.image('redis').withRun { container ->
            docker.image('maven').inside("--link ${container.id}:redis") {
                sh 'cat artifact.txt'
                sh 'ls -lah'
            }
        }
    }

    stage('Deploy') {
    }
}
