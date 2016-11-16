#!/usr/bin/env groovy

parallel(jdk7: {
    node('docker') {
            docker.image('openjdk:7').inside {
                echo 'im building'
                sh 'echo "HELLO" > artifact.txt'
                stash name: 'thething', includes: 'artifact.txt'
            }
        }
    },
    jdk8: {
        node('docker') {
            docker.image('openjdk:8').inside {
                echo 'im building on 8'
            }
        }
    }
})

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
