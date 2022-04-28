#!/usr/bin/env groovy

library identifier: 'jenkins-shared-lib@master', retriever: modernSCM(
        [$class: 'GitSCMSource',
         remote: 'https://github.com/Pratyush3997/new-maven-app.git',
         credentialsId: '5557fd79-4430-490a-8945-2b909db39e38'
        ]
)


def gv

pipeline {
    agent any
    tools {
        maven 'Maven-3.8.5'
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
                    buildJar()
                }
            }
        }
        stage("build and push image") {
            steps {
                script {
                    buildImage 'testp123/demo-repo-1:jma-3.0'
                    dockerLogin()
                    dockerPush 'testp123/demo-repo-1:jma-3.0'
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
    }
}
