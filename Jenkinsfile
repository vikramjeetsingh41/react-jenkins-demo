#!/usr/bin/env groovy

node('node') {

    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){
          checkout scm
       }

       stage('install'){
         sh 'node -v'
         sh 'npm install'
       }

       stage('Deploy'){
         echo 'Push to Repo'
       }

       stage('Cleanup'){
         echo 'prune and cleanup'
         sh 'npm prune'
         sh 'rm node_modules -rf'

         mail body: 'project build successful',
                     from: 'vsingh@palo-it.com',
                     replyTo: 'vsingh@palo-it.com',
                     subject: 'project build successful',
                     to: 'vsingh@palo-it.com'
       }



    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

}