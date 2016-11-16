#!/usr/bin/env groovy


node('docker') {
    def container
    stage('Build') {
        checkout scm
        container = docker.build('clusterhq:dameetup')
    }

    stage('Test') {
        container.withRun {
            sh 'curl http://localhost'
        }
    }

    stage('Deploy') {
        docker.withRegistry {
            container.push()
        }
    }
}
