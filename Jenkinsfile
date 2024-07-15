#!/usr/bin/env groovy

pipeline {
    // agent any
    agent {
        docker { 
                    image 'ubuntu:latest'
                    args '-u root'
                }
    }
    stages {

        stage('Print hello') {
            steps {
                echo 'Hello world!'
            }
        }
        stage('Setup') {
            steps {
                sh '''
                    apt-get update
                    apt-get install -y python3 python3-pip git
                    pip -h
                '''
            }
        }
        stage('Get Python SBOM'){
            steps{
                sh 'apt-get install git'
                sh 'git clone https://github.com/CycloneDX/cyclonedx-python.git'
                sh 'pip install cyclonedx-bom'
                sh 'cd cyclonedx-python'
                sh 'cyclonedx-py environment -o bom.json'
                sh 'cat bom.json'
            }
        }

    }
}