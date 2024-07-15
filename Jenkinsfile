#!/usr/bin/env groovy

pipeline {
    // agent any
    agent {
        docker { image 'ubuntu:latest'}
    }
    stages {
        stage('Print hello') {
            steps {
                echo 'Hello world!'
            }
        }

        stage('Get Python SBOM'){
            steps{
                sh 'sh “chown -R 1000 ./”'
                sh 'sudo apt install git'
                sh 'git clone https://github.com/CycloneDX/cyclonedx-python.git'
                sh 'pip install cyclonedx-bom'
                sh 'cd cyclonedx-python'
                sh 'cyclonedx-py environment -o bom.json'
                sh 'cat bom.json'
            }
        }

    }
}