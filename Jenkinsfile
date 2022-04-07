#!/usr/bin/env groovy

def gv

pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
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
                    echo "Deploying the application..."                   
                }
            }
        }
    }
}
