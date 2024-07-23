#!/usr/bin/env groovy

pipeline {
    parameters { 
        booleanParam(name: 'SBOM_STUDIO', defaultValue: true, description: 'Enable Cybeats SBOM Studio')
    }
    agent none
    stages {
        // stage('Node') {
        //     agent {
        //     docker { 
        //                 image 'node:20.15.1-bullseye' 
        //                 args '-u root'
        //         }
        //     }
        //     steps {
        //         sh 'node --version'
        //         sh 'npm --version'
        //         sh 'npm install --global @cyclonedx/cyclonedx-npm'
        //         sh 'apt install -y git'
        //         script {
        //             if (fileExists('./cyclonedx-node-npm')){
        //                 echo 'folder already exists, removing...'
        //                 sh 'rm -r cyclonedx-node-npm'
        //             }
        //         }
        //         // sh 'rm -r cyclonedx-node-npm'
        //         sh 'git clone https://github.com/CycloneDX/cyclonedx-node-npm.git'
        //         sh 'cyclonedx-npm -h'
        //         dir ('cyclonedx-node-npm'){
        //            sh 'pwd' 
        //            sh 'ls'
        //            sh 'npm install'
        //            sh 'cyclonedx-npm --output-file cdx-npm-sbom.json'
        //            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
        //             sbomStudio filePath: 'cdx-npm-sbom.json',
        //                         manufacturerId: 'Cybeats', 
        //                         pkgType: 'npm', 
        //                         sbomComponentName: 'CycloneDX-NPM-Test', 
        //                         sbomComponentNamespace: '', 
        //                         sbomComponentVersion: '1.0.0', 
        //                         subType: 'application', 
        //                         supplierId: 'Cybeats'
        //             }
                    
        //         }
        //     }
        // }
        // stage('Python'){
        //     agent {
        //             docker { 
        //                         image 'python:3.10-bullseye' 
        //                         args '-u root'
        //             }
        //     } 
        //     steps {
        //         sh 'python3 --version'
        //         sh 'pip --version'
        //         sh 'pip install cyclonedx-bom'
        //         sh 'apt install -y git'
        //         script {
        //             if (fileExists('./cyclonedx-python')){
        //                 echo 'folder already exists, removing...'
        //                 sh 'rm -r cyclonedx-python'
        //             }
        //         }
        //         // sh 'rm -r cyclonedx-python'
        //         sh 'git clone https://github.com/CycloneDX/cyclonedx-python.git'
        //         sh 'cyclonedx-py -h'
        //         dir('cyclonedx-python'){
        //             sh 'cyclonedx-py environment -o cdx-python-sbom.json'
        //             catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
        //             sbomStudio filePath: 'cdx-python-sbom.json',
        //                         manufacturerId: 'Cybeats', 
        //                         pkgType: 'pypi', 
        //                         sbomComponentName: 'CycloneDX-Python-Test', 
        //                         sbomComponentNamespace: '', 
        //                         sbomComponentVersion: '1.0.0', 
        //                         subType: 'application', 
        //                         supplierId: 'Cybeats'
        //             }
                    
        //         }
        //     }
            
        // }
        // stage('Go'){
        //     agent {
        //             docker { 
        //                         image 'golang:1.23rc2-bookworm' 
        //                         args '-u root'
        //             }
        //     } 
        //     steps {
        //         sh 'go version'
        //         sh 'go install github.com/CycloneDX/cyclonedx-gomod/cmd/cyclonedx-gomod@latest'
        //         script {
        //             if (fileExists('./cyclonedx-gomod')){
        //                 echo 'folder already exists, removing...'
        //                 sh 'rm -r cyclonedx-gomod'
        //             }
        //         }
        //         // sh 'rm -r cyclonedx-gomod'
        //         sh 'git clone https://github.com/CycloneDX/cyclonedx-gomod.git'
        //         sh 'cyclonedx-gomod -h'
        //         dir('cyclonedx-gomod'){
        //             sh 'cyclonedx-gomod mod -output cdx-gomod.cdx.json -json=True'
        //             sh 'ls'
        //             catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
        //             sbomStudio filePath: 'cdx-gomod.cdx.json',
        //                         manufacturerId: 'Cybeats', 
        //                         pkgType: 'golang', 
        //                         sbomComponentName: 'CycloneDX-Golang-Test', 
        //                         sbomComponentNamespace: '', 
        //                         sbomComponentVersion: '1.0.0', 
        //                         subType: 'application', 
        //                         supplierId: 'Cybeats'
        //             }
        //         }
        //     }
            
        // }
        // stage('Rust'){
        //     agent {
        //             docker { 
        //                         image 'rust:1.79-bullseye' 
        //                         args '-u root'
        //             }
        //     } 
        //     steps {
        //         sh 'cargo version'
        //         sh 'cargo install cargo-cyclonedx'
        //         script {
        //             if (fileExists('./cyclonedx-rust-cargo')){
        //                 echo 'folder already exists, removing...'
        //                 sh 'rm -r cyclonedx-rust-cargo'
        //             }
        //         }
        //         sh 'git clone https://github.com/CycloneDX/cyclonedx-rust-cargo.git'
        //         sh 'cargo cyclonedx -h'
        //         dir('cyclonedx-rust-cargo'){
        //             sh 'cargo cyclonedx --manifest-path cargo-cyclonedx/Cargo.toml -f json'
        //             sh 'ls'
        //             sh 'ls cargo-cyclonedx/'
        //             catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
        //             sbomStudio filePath: 'cargo-cyclonedx/cargo-cyclonedx.cdx.json',
        //                         manufacturerId: 'Cybeats', 
        //                         pkgType: 'cargo', 
        //                         sbomComponentName: 'CycloneDX-Rust-Test', 
        //                         sbomComponentNamespace: '', 
        //                         sbomComponentVersion: '1.0.0', 
        //                         subType: 'application', 
        //                         supplierId: 'Cybeats'
        //             }
        //         }
        //     }
            
        // }
        stage('Java'){
            agent {
                    docker { 
                                image 'maven:3.9.8-amazoncorretto-17-debian-bookworm' 
                                args '-u root'
                    }
            } 
            steps {
                sh 'apt install -y git'
                sh 'git --help'
                sh 'mvn -v'
                script {
                    if (fileExists('./cyclonedx-maven-plugin')){
                        echo 'folder already exists, removing...'
                        sh 'rm -r cyclonedx-maven-plugin'
                    }
                }
                sh 'git clone https://github.com/CycloneDX/cyclonedx-maven-plugin.git'
                dir('cyclonedx-maven-plugin'){
                    sh 'ls'
                    sh 'mvn clean install'
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'cyclonedx-maven-plugin/target/bom.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'cargo', 
                                sbomComponentName: 'CycloneDX-Java-Test', 
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