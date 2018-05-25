#!/usr/bin/env groovy

node {

    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){
          checkout scm
       }

       stage('install'){
         sh 'node -v'
         sh 'sudo npm install'
       }

       stage('Deploy'){
         echo 'Push to Repo'
       }

       stage('Cleanup'){
         echo 'prune and cleanup'
         sh 'npm prune'
         sh 'rm -R node_modules'
       }

    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

}