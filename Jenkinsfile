pipeline {
    agent none
    stages {
        stage('lint-css') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '--privileged'
              }
          }
            steps {
                sh 'ls -al'
                sh 'mkdir some'
                sh 'node --version'
                sh 'npm --version'
                sh 'yarn version'
                sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
    }
}
