#!/usr/bin/env groovy

pipeline {
    parameters { 
        booleanParam(name: 'SBOM_STUDIO', defaultValue: true, description: 'Enable Cybeats SBOM Studio')
    }
    agent none
    stages {
        stage('Node') {
            agent {
            docker { 
                        image 'node:20.15.1-bullseye' 
                        args '-u root'
                }
            }
            steps {
                sh 'node --version'
                sh 'npm --version'
                sh 'npm install --global @cyclonedx/cyclonedx-npm'
                sh 'apt install -y git'
                // sh 'rm -r cyclonedx-node-npm'
                sh 'git clone https://github.com/CycloneDX/cyclonedx-node-npm.git'
                sh 'cyclonedx-npm -h'
                dir ('cyclonedx-node-npm'){
                   sh 'pwd' 
                   sh 'ls'
                   sh 'npm install'
                   sh 'cyclonedx-npm --output-file cdx-npm-sbom.json'
                   catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'cdx-npm-sbom.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'npm', 
                                sbomComponentName: 'CycloneDX-NPM-Test', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '1.0.0', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                    }
                    
                }
            }
        }
        stage('Python'){
            agent {
                    docker { 
                                image 'python:3.10-bullseye' 
                                args '-u root'
                    }
            } 
            steps {
                sh 'python3 --version'
                sh 'pip --version'
                sh 'pip install cyclonedx-bom'
                sh 'apt install -y git'
                // sh 'rm -r cyclonedx-python'
                sh 'git clone https://github.com/CycloneDX/cyclonedx-python.git'
                sh 'cyclonedx-py -h'
                dir('cyclonedx-python'){
                    sh 'cyclonedx-py environment -o cdx-python-sbom.json'
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'cdx-python-sbom.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'pypi', 
                                sbomComponentName: 'CycloneDX-Python-Test', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '1.0.0', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                    }
                    
                }
            }
            
        }
        stage('Go'){
            agent {
                    docker { 
                                image 'golang:1.23rc2-bookworm' 
                                args '-u root'
                    }
            } 
            steps {
                sh 'go version'
                sh 'go install github.com/CycloneDX/cyclonedx-gomod/cmd/cyclonedx-gomod@latest'
                // sh 'rm -r cyclonedx-gomod'
                sh 'git clone https://github.com/CycloneDX/cyclonedx-gomod.git'
                sh 'cyclonedx-gomod -h'
                dir('cyclonedx-gomod'){
                    sh 'cyclonedx-gomod mod -output cdx-gomod.cdx.json -json=True'
                    sh 'ls'
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'cdx-gomod.cdx.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'golang', 
                                sbomComponentName: 'CycloneDX-Golang-Test', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '1.0.0', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                    }
                }
            }
            
        }
    }
}