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
                archiveArtifacts artifacts: 'dist/nodejs-test.zip'
            }
        }
    }
}
