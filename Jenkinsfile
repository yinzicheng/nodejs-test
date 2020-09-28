pipeline {
    agent any
    stages {
        stage('npm install') {
            steps {
                echo 'install dependencies'
                sh 'npm build'
                // archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
    }
}
