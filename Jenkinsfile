#!/usr/bin/env groovy

pipeline {
    agent {
        docker { image 'ubuntu:latest' }
    }
    stages {
        stage('Print hello') {
            steps {
                echo 'Hello world!'
            }
        stage('Get Python SBOM')
            steps{
                sh 'git clone https://github.com/CycloneDX/cyclonedx-python.git'
            }
        }
    }
}