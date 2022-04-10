#!/usr/bin/env groovy

def gv

pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    gv.buildJar()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    gv.deployApp()
                    sshagent(['3.109.47.42']) {
                        sh 'ssh -o StrictHostKeyChecking=0 ec2-user@3.109.47.42'
                    }
                }
            }
        }
    }
}
