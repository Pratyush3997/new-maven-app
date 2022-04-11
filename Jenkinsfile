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
                    sshagent(['ec2-server-key']) {
                        sh 'ssh -o StrictHostKeyChecking=no ec2-user@65.0.102.246:3000'
                    }
                }
            }
        }
    }
}
