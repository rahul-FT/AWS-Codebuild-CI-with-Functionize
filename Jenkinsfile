pipeline {
    agent none
    stages {
        stage('lint-css') {
            agent { docker 'ubuntu' }
            steps {
                sh 'ls -al'
                sh 'whoami'
                sh 'apt-get update'
                sh 'apt-get nodejs'
                // sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
        stage('Stage 2') {
            agent { docker 'node:9.11.1' }
            steps {
                echo 'Hello, From Second Stage'
                sh 'node --version'
            }
        }
    }
}
