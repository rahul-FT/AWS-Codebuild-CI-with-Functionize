pipeline {
    agent none
    stages {
        stage('lint-css') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'ls -al'
                sh 'npm install'
                sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
    }
}
