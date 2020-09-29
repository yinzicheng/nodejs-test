pipeline {
    agent any
    stages {
        stage('npm install') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS 14.11.0') {
                    sh 'npm config ls'
                }
            }
        }
    }
}
