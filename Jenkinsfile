pipeline {
    agent any
    environment {
        DB_ENGINE = 'sqlite'
        AWS_ACCESS_KEY_ID = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stages {
        withCredentials([usernamePassword(credentialsId: 'jenkins-bitbucket-common-creds', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]) {
            stage('Build') {
                steps {
                    sh 'printenv'
                    echo "DB_ENGINE is ${DB_ENGINE}"
                    echo "AWS_ACCESS_KEY_ID is ${AWS_ACCESS_KEY_ID}"
                    echo "AWS_SECRET_ACCESS_KEY is ${AWS_SECRET_ACCESS_KEY}"
                    echo "BITBUCKET user is ${USERNAME}, BITBUCKET password is ${USERPASS}"
                }
            }
        }
    }
}
