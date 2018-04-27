pipeline {
    agent none
    // stages {
    //     stage('lint-css') {
    //       agent {
    //           docker {
    //             image 'node:9.11.1'
    //             args  '-u root'
    //           }
    //       }
    //         steps {
    //             sh 'npm install'
    //             sh './node_modules/gulp/bin/gulp.js lint-css'
    //         }
    //     }
    // }
    // stages {
    //     stage('lint-js') {
    //       agent {
    //           docker {
    //             image 'node:9.11.1'
    //             args  '-u root'
    //           }
    //       }
    //         steps {
    //             sh 'npm install'
    //             sh './node_modules/gulp/bin/gulp.js lint-js'
    //         }
    //     }
    // }
    // stages {
    //     stage('Deploy-Staging') {
    //       agent {
    //           docker {
    //             image 'node:9.11.1'
    //             args  '-u root'
    //           }
    //       }
    //         steps {
    //             sh 'apt-get update -qq && apt-get install -y -qq sshpass'
    //             sh 'sshpass -ptoor ssh -o StrictHostKeyChecking=no root@35.192.162.132 "cd /usr/share/nginx/html/staging-jenkins-rvsharma.com && git pull -f'
    //         }
    //     }
    // }
    stages {
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
              sh 'cd functionizecli && ls -al'
              sh 'cd functionizecli && mv config-sample.js config.js'
              sh 'cd functionizecli && sed -i \'s/"xxxxxxxxxx"/"9dd73eb3e026a06c809eaa09cd51fdb5"/g\' config.js'
              sh 'cd functionizecli && sed -i \'s/"xxxxxx"/"ba3f54fb653e995f15c107ed5d876975"/g\' config.js'
              sh 'echo "Running Orchestrations"'
              sh 'export DEPLOYMENT_ID=6868c7a2bf517501f4ecf65f5d5a84dc'
              sh 'echo $DEPLOYMENT_ID'
              sh '/usr/local/bin/functionize run-deployment --depID $DEPLOYMENT_ID'
              // sh 'wget -O - https://bitbucket.org/functionize/functionizecli/raw/master/ThirdParty_run.sh | bash'
            }
        }
    }
    // stages {
    //     stage('Deploy-Production') {
    //       agent {
    //           docker {
    //             image 'node:9.11.1'
    //             args  '-u root'
    //           }
    //       }
    //         steps {
    //             sh 'apt-get update -qq && apt-get install -y -qq sshpass'
    //             sh 'sshpass -ptoor ssh -o StrictHostKeyChecking=no root@35.192.162.132 "cd /usr/share/nginx/html/production-jenkins-rvsharma.com && git pull -f'
    //         }
    //     }
    // }
}
