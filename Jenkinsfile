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
                sh 'pwd'
                sh 'ls'
                // sh 'apt-get install git'
                // sh 'apt-get install -y pipx'
                // sh 'git clone https://github.com/CycloneDX/cyclonedx-python.git'
                // sh 'pipx install cyclonedx-bom'
                // sh 'pipx ensurepath'
                // sh 'cyclonedx-py -h'
                // sh 'cd cyclonedx-python'
                // sh 'cyclonedx-py environment -o bom.json'
                // sh 'cat bom.json'
            }
        }

    }
}