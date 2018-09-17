#!/usr/bin/env groovy

pipeline {
    agent none
    
    stages {
        stage('Build') {
            agent { docker 'alpine' }
            steps {
                echo 'I am building'
                sh 'uname -a'
            }
        }
        stage('Test') {
            agent { docker 'maven' }
            steps {
                sh 'mvn --version'
            }
        }
        stage('Deploy') {
            agent { docker 'alpine' }
            steps {
                echo 'Deploying to serverless cloud containers etc'
            }
        }
        
    }
}
