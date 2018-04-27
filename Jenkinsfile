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
                sh 'npm install'
                sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
        stage('lint-js') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'npm install'
                sh './node_modules/gulp/bin/gulp.js lint-js'
            }
        }
        stage('Deploy-Staging') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'apt-get update -qq && apt-get install -y -qq sshpass'
                sh 'sshpass -ptoor ssh -o StrictHostKeyChecking=no root@35.192.162.132 "cd /usr/share/nginx/html/staging-jenkins-rvsharma.com && git pull -f"'
            }
        }
        stage('Functionize-CLI') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
              sh 'rm -rf functionizecli'
              sh 'git clone https://functionize@bitbucket.org/functionize/functionizecli.git'
              sh 'cd functionizecli && npm install'
              sh 'cd functionizecli && npm install -g'
              sh 'cd functionizecli && mv config-sample.js config.js'
              sh 'cd functionizecli && sed -i \'s/"xxxxxxxxxx"/"6444c1a2469d7dc61bd8a3f31f703653"/g\' config.js'
              sh 'cd functionizecli && sed -i \'s/"xxxxxx"/"1588e875c1e34df941091f393251fa26"/g\' config.js'
              sh 'echo "Running Orchestrations"'
              sh 'export DEPLOYMENT_ID=b5e27cff23ad2cd07cd5f778e327d0ae && wget -O - https://bitbucket.org/functionize/functionizecli/raw/master/ThirdParty_run.sh | bash'
            }
        }
        stage('Deploy-Production') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'apt-get update -qq && apt-get install -y -qq sshpass'
                sh 'sshpass -ptoor ssh -o StrictHostKeyChecking=no root@35.192.162.132 "cd /usr/share/nginx/html/production-jenkins-rvsharma.com && git pull -f"'
            }
        }
    }
  }
