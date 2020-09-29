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
                zip zipFile: "dist/nodejs-test.zip", archive: true
                archiveArtifacts artifacts: 'dist/nodejs-test.zip'
            }
        }
    }
}
