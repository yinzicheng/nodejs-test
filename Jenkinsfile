pipeline {
    agent any
    stages {
        stage('npm install') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS 14.11.0') {
                    sh 'npm install'
                }
            }
        }
        stage('build') {
            steps {
                sh 'rm -rf dist && mkdir dist'
                zip zipFile: 'dist/nodejs-test.zip', archive: true
                archiveArtifacts artifacts: 'dist/nodejs-test.zip'
            }
        }
        stage('deploy'){
            when{
                branch 'master'
            }
            steps{
                script{
                    def remote = [:]
                    remote.name = 'node1'
                    remote.host = '192.168.1.130'
                    remote.user = 'vagrant'
                    remote.password = 'vagrant'
                    remote.allowAnyHosts = true
                    stage('Remote SSH') {
                        sshPut remote: remote, from: 'dist/nodejs-test.zip', into: '/tmp'
                        sshCommand remote: remote, command: '''
                            rm -rf /vagrant/jenkins/deploy/nodejs-test &&
                            mkdir -p /vagrant/jenkins/deploy/nodejs-test &&
                            unzip /tmp/nodejs-test.zip -d /vagrant/jenkins/deploy/nodejs-test &&
                            /home/vagrant/.nvm/versions/node/v14.12.0/bin/npm start --prefix /vagrant/jenkins/deploy/nodejs-test
                        '''
                    }
                }
            }
        }
    }
}
