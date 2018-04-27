pipeline {
    agent none
    stages {
        stage('lint-css') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '- root'
              }
          }
            steps {
                sh 'ls -al'
                sh 'mkdir some'
                sh 'npm install -g'
                sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
    }
}
