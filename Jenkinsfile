pipeline {
    agent none
    stages {
        stage('lint-css') {
          agent {
              docker {
                image 'maven:3-alpine'
                args  '-v /tmp:/tmp'
              }
          }
            steps {
                sh 'ls -al'
                sh 'node --version'
                sh 'npm --version'
                sh 'yarn version'
                // sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
    }
}
