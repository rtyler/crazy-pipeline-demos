#!/usr/bin/env groovy

node('docker') {
    stage('Build') {
        docker.image('alpine').inside {
            echo 'im building'
            sh 'echo "HELLO" > artifact.txt'
            stash name: 'thething', includes: 'artifact.txt'
        }
    }
}

node('docker') {
    stage('Test') {
        docker.image('redis').withRun { container ->
            docker.image('maven').inside("--link ${container.id}:redis") {
                unstash 'thething'
                sh 'cat artifact.txt'
                sh 'ls -lah'
            }
        }
    }

    stage('Deploy') {
    }
}
